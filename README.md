# quest-submissions

## Chapter 1 Day 1 Quests

Fill in your answers here
Smart contract is a set of programs or rules made by a developer, enabling users to interact in the blockchain.
Cadence is the smart contract programming language in Flow whereas Rust is the same for Solana,
Playground is the place where smart contracts are written, where projects are designed, performed and tested before deplyed on "Main Net".
Script is a Read only program and Transaction is a Read and Write program.
A Blockchain is a decentralized system of data arranged in linked blocks and secured against any alteration or counterfeiting. These blocks thus form a blockchain which stores all the history of their interactions, of their exchanges.


## Chapter 2 Day 2 Quests

Please answer in the language of your choice.

Explain why we wouldn't call changeGreeting in a script.
As far as I understand the definition of a script, we can only read a script, we could therefore call changeGreeting in a transaction as well.


What does the AuthAccount mean in the prepare phase of the transaction?
The AuthAccount type allows to access to data stored in my account : in my comprehension it represents my approval (my signature, my stamp) for transaction in my account. The prepare phase is the pathway wherein we can access to the data in my account.


What is the difference between the prepare phase and the execute phase in the transaction?
As explained above for the prepare phase during the transaction, the execution phase differs by the fact that we can call functions and change data of the blockchain but does not allow access to my account. 


This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

Add two new things inside your contract:

A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
pub contract HelloWorld {

    pub var greeting: String
    pub var myNumber: Int

    init() {
        self.greeting = "Hello, World!"
        self.myNumber = 0
    }
pub fun changeGreeting(newGreeting: String) {
    self.greeting = newGreeting
}

}


A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

pub fun updatemyName(newNumber: Int)  
{
    self.myNumber = newNumber
}

Add a script that reads myNumber from the contract

import HelloWorld from 0x01

pub fun main(): Int {
    return HelloWorld.myNumber
}    

Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

import HelloWorld from 0x01

transaction(myNewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.updatemyName(newNumber:myNewNumber)
  }
}



CHAPTER 3

Workshop 3/8 Chapter 3 Day 1 - Resources

Quests

As always, feel free to answer in the language of your choice.

1- In words, list 3 reasons why structs are different from resources.
    . Structs can be copied, which is impossible for resources.
    . Structs could be lost or overwritten what is impossible for resources.
    . Resources can not be created whenever I want unlike Structs that could be.

2- Describe a situation where a resource might be better to use than a struct.
    I have to be extremely explicit about how I handle a resource (for example when I move them), what make resources extremely secure.

3- What is the keyword to make a new resource?
    create

4- Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?
    NO! resource can only be created inside a contract.
    
5- What is the type of the resource below?

pub resource Jacob {

}

It is string resource type


6- Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.

pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): Jacob { // there is 1 here
        let myJacob = Jacob() // there are 2 here
        return myJacob // there is 1 here
    }
}


pub contract Test {

    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob {
        let myJacob <- create Jacob ()
        return <- myJacob
    }
}

Workshop 4/8 Chapter 3 Day 2 - Resources / References

Quests
1. Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.

pub contract KamaraTest {

    pub var arrayOfNFTs: @[NFT]
    pub var dictionaryOfNFTs: @{String: NFT}

    pub resource NFT {
        pub let message: String
        init() {
            self.message = "Hello, Welcome in your Gallery!"
        }
    }

    pub fun addNFT(NFT: @NFT) {
        let key = NFT.message
        let oldNFT <- self.dictionaryOfNFTs[key] <- NFT
        destroy oldNFT
    }

    
    pub fun removeNFT(key: String): @NFT {
        let NFT <- self.dictionaryOfNFTs.remove(key: key) ?? panic("Could not find the NFT!")
        return <- NFT
    }

        init() {
        self.arrayOfNFTs <- []
        self.dictionaryOfNFTs <- {}
    }

}

Workshop 4/8 Chapter 3 Day 3 - References

Quests

1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

3. Explain, in your own words, why references can be useful in Cadence.





