# ETH:Creating Token 
This Solidity program provides simple functionality for creating tokens on the blockchain.

## Description
This program consists of simple functions and variables which help in mapping data, minting tokens, and burning resources as necessary. It includes checks to prevent excessive minting and burning of tokens.

## Getting Started
This program contains straightforward functions and variables designed for mapping data, minting tokens, and burning resources as necessary.

### Executing program
To run this program, you can utilize Remix, an online Solidity IDE. Begin by navigating to the Remix website at Remix Ethereum.

Once you're on the Remix website, initiate a new file by selecting the "+" icon in the left-hand sidebar. Save the file with a .sol extension (for instance, MyToken.sol). Then, copy and paste the provided code into the file.

solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken{
    
    // public variables here
    string public tokenName = "Philip";
    string public tokenAbbrv = "PHIL";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances; 

    // mint function
    function mint(address _address, uint _value) public {
        // Ensure the value to be minted is not more than 10,000 tokens
        require(_value <= 10000, "Cannot mint more than 10,000 tokens at a time");

        // Increase the total supply by the minted amount
        totalSupply += _value;
        // Increase the balance of the specified address
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        // Ensure the address has enough tokens to burn
        require(balances[_address] >= _value, "Insufficient balance to burn");
        // Ensure the value to be burned is not more than 10,000 tokens
        require(_value <= 10000, "Cannot burn more than 10,000 tokens at a time");

        // Decrease the total supply by the burned amount
        totalSupply -= _value;
        // Decrease the balance of the specified address
        balances[_address] -= _value;
    }
}


To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" (or whatever the file name is) button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

After deployment, you can interact with the contract using the default addresses provided. You can mint new tokens to an address and burn tokens from an address. Each address acts as a different user, allowing you to perform various operations on it.

## Authors

Aditi Rajput
[@Chandigarh University](https://www.linkedin.com/in/aditi-rajput-b9360720b/)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
