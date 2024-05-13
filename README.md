To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., project.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.13;

contract Smart_Contract_Project {

    address public GregFlorence;
    uint public amount;

    constructor() {
        GregFlorence = msg.sender;
    }

   
    function incremetAmount(uint _newAmount) public {

        require(_newAmount > 1, "Invalid Amount");

        assert(msg.sender == GregFlorence);

        amount += _newAmount;
    }

    
    function doubleAmount() public {
        assert(msg.sender == GregFlorence);
        amount *= 2;
    }


    function withdraw(uint _amount) public {

        require(_amount > 1, "Invalid amount.");

        assert(msg.sender == GregFlorence);

        if(_amount > amount){
            revert("Not enought balance.");
        }

        amount -= _amount;
    }
}
