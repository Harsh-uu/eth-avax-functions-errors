# Functions and Errors handling contract

This Solidity program is a simple "Fund Transaction" program that demonstrates the knowledge of error handeling(revert, require, assert) functionality in Solidity programming language.

# Description

This is the program to demosatrate the use of revert, require, assert in solidity.

The contract is named wallet and is specified to be licensed under the MIT license. The contract uses a Solidity version equal to or greater than 0.8.18.

### Contract Variables:

totalAmount: A public unsigned integer variable that represents the total balance of the wallet. It stores the amount of funds available in the wallet. owner: An address variable that represents the owner of the wallet. It is set to the address of the contract deployer.

### Constructor:

The constructor is defined with a single parameter uint \_totalAmount. When the contract is deployed, the \_totalAmount value is passed as an argument. Inside the constructor, the totalAmount variable is initialized with the provided \_totalAmount value. The owner variable is set to the address of the contract deployer, accessed using msg.sender.

### Function: transfer

This function is used to transfer funds from the wallet to a specified recipient address (sendTo).

It takes three parameters: amount: The amount of funds to be transferred. tax: The tax or fee to be deducted from the transferred amount. sendTo: The address to which the funds will be transferred.

Within the function, the amount and tax are added together to calculate amountTOBeDeducted, representing the total amount to be deducted from the totalAmount balance. The totalAmount is decreased by amountTOBeDeducted to reflect the deduction from the wallet balance. The function includes a check to ensure that the tax value is less than the amount value, and if not, it reverts the transaction with an error message. It also includes a requirement that the amountTOBeDeducted value is less than the current totalAmount, ensuring that the wallet has sufficient funds to cover the transfer. Finally, an assert statement is used to verify that the owner address is not the same as the sendTo address. This ensures that the owner cannot transfer funds to themselves.

### Function: getamount

This function is a simple getter function that returns the current value of totalAmount. It is marked as view to indicate that it does not modify the contract's state. Overall, this contract provides a basic functionality of a wallet with a transfer method that deducts a specified tax from the transferred amount and performs validation checks.

## Authors

Harsh Gupta
