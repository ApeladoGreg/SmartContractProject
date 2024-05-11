To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., project.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: GPL-3.0 pragma solidity 0.8.13;

// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.13;

contract Smart_Contract_Project {
    address public GregFlorence;
    uint public amount;

    constructor() {
        GregFlorence = msg.sender;
        amount = 300;
    }

   
    function setAmount(uint _newAmount) public {
        require(msg.sender == GregFlorence, "Only the Owner can set the amount");
        amount = _newAmount;
    }

    
    function doubleAmount() public {
        uint newAmount = amount * 200;
        assert(newAmount >= amount); 
        amount = newAmount;
    }


    function withdraw(uint _amount) public {
        require(_amount <= address(this).balance, "Sorry, Insufficient Balance!");
        payable(msg.sender).transfer(_amount);
    }
}
