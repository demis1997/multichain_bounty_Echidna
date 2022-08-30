# multichain_bounty_Echidna
 immunefi bug bounty using echidna and slither

The first test we are making is with this part of the code, this is the transfer function which checks that your balance has enough to make the transfer and increases the value of the person you are sending to by the amount you set

```
    function transfer(address to, uint256 value) external override returns (bool) {
        require(to != address(0) || to != address(this));
        uint256 balance = balanceOf[msg.sender];
        require(balance >= value, "AnyswapV3ERC20: transfer amount exceeds balance");

        balanceOf[msg.sender] = balance - value;
        balanceOf[to] += value;
        emit Transfer(msg.sender, to, value);

        return true;
    }
```
and this:
```
   function setVaultOnly(bool enabled) external onlyVault {
        _vaultOnly = enabled;
    }
```


```
    function transfer(address to, uint256 value) external override returns (bool) {
        require(to != address(0) || to != address(this));
        uint256 balance = balanceOf[msg.sender];
        require(balance >= value, "AnyswapV3ERC20: transfer amount exceeds balance");

        balanceOf[msg.sender] = balance - value;
        balanceOf[to] += value;
        emit Transfer(msg.sender, to, value);

        return true;
    }
    function echidna_test_balance() public view returns (bool) {
        return balances[echidna_caller] < 10000 && _vaultOnly = disabled;
    }
```
