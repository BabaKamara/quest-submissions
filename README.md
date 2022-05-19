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
(need some help to start : how to do it ? I tried this :   
pub var: Int
  init() {
  Int = 0
  let myNumber = 0


A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber

Add a script that reads myNumber from the contract

Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.
