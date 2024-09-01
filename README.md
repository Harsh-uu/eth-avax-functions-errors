# Wallet Contract - Functions and Error Handling
This Solidity program is a simple "Wallet" contract that demonstrates the use of error handling (revert, require, assert) in Solidity. The purpose of this program is to showcase how error handling and validation checks are implemented within a smart contract on the Ethereum blockchain.

## Description
This program is a smart contract written in Solidity that functions as a basic wallet. It allows the owner to manage a balance and transfer funds to a recipient address with a specified tax. The contract utilizes revert, require, and assert statements for error handling to ensure proper and secure transactions. This program serves as a practical example for developers to understand error handling and secure programming practices in Solidity.

## Getting Started
### Executing Program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at Remix IDE.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Wallet.sol). Copy and paste the following code into the file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract Wallet {
    uint public totalAmount;  // Stores the total balance of the wallet
    address public owner;     // Stores the address of the owner of the wallet

    // Constructor initializes the contract with the specified total amount and sets the owner
    constructor(uint _totalAmount) {
        totalAmount = _totalAmount;
        owner = msg.sender;  // Sets the deployer as the owner of the contract
    }

    // Function to transfer funds from the wallet to a specified recipient
    function transfer(uint amount, uint tax, address sendTo) public {
        uint amountToBeDeducted = amount + tax;  // Calculate the total amount to be deducted (amount + tax)
        
        // Revert the transaction if the tax is greater than or equal to the amount
        if (tax >= amount) {
            revert("Tax should be less than amount to be transferred");
        }
        
        // Ensure the total balance is sufficient for the transfer
        require(amountToBeDeducted <= totalAmount, "Amount + tax should be less than or equal to current balance");
        
        // Ensure the owner is not transferring to themselves
        assert(owner != sendTo);
        
        // Deduct the total amount (amount + tax) from the wallet's total balance
        totalAmount -= amountToBeDeducted;
    }

    // Getter function to retrieve the current total balance of the wallet
    function getAmount() public view returns (uint) {
        return totalAmount;
    }
}

```
### Compiling and Deploying the Code
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Wallet.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Wallet" contract from the dropdown menu, and then click on the "Deploy" button.

### Interacting with the Contract
Once the contract is deployed, you can interact with it by calling the transfer and getAmount functions:

* transfer Function: To transfer funds, enter the amount, tax, and sendTo parameters, then click on the "transact" button. The contract will perform necessary checks and either execute or revert the transaction based on the conditions.

* getAmount Function: To check the current balance of the wallet, click on the getAmount function. The balance will be displayed without modifying the contract's state.

## Authors
Harsh Gupta  
[@harsh-uu](https://github.com/harsh-uu)
