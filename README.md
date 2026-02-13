# Require-

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;
contract SmartWalletContract {

      mapping(address => uint) public balanceReceived;

      function receiveMoney() public payable{
        balanceReceived[msg.sender] += msg.value;
      }

      function withdrawMoney(address payable _to, uint _amount) public {
        require(_amount <= balanceReceived[msg.sender],"Not enough funds, aborting");
        balanceReceived[msg.sender] -= _amount;
        _to.transfer(_amount);
      }

}

contract AssertEample {

    mapping(address => uint8) public balanceReceived;

     function receiveMoney() public payable {
        assert(msg.value == uint8(msg.value));
        balanceReceived[msg.sender] += uint8(msg.value);

     }

  function withdrawMoney(address payable _to, uint8 _amount) public {
      require(_amount <= balanceReceived[msg.sender], "Not enough funds, aborting!");
    balanceReceived[msg.sender] -= _amount;
         _to.transfer(_amount);
    } 

}
