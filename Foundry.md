# 1、安装

# 2、创建新项目

# 3、在已有的项目使用

# 4、依赖

# 5、项目布局

# 6、测试

## 6.1编写测试

​		Foundry框架提供的测试是用solidity编写的，有一个Test.sol的测试库，我们进行测试编写的时候，可以写一个测试合约，然后继承Foundry的Test.sol。

`案例`

```solidity
pragma solidity 0.8.10;

import "forge-std/Test.sol";//引入测试库

contract ContractBTest is Test {
    uint256 testNumber;

    function setUp() public {
        testNumber = 42;
    }

    function testNumberIs42() public {
        assertEq(testNumber, 42);
    }

    function testFailSubtract43() public {
        testNumber -= 43;
    }
}

```

这是一个标准测试合约的demo，分析一下他们的做法

* 引入测试库

* 定义测试合约

  * 设置setUp()函数

  * 设置成功环境测试函数
  * 设置失败环境测试函数

### 6.1.1引入测试库

```solidity
import "forge-std/Test.sol";
```

### 6.1.2定义测试函数

测试函数式需要继承Foundry测试库的Test.sol，一个测试合约中如果没有以test开头的测试用例，则不会执行这个测试合约。

`setUp`：在每个测试用例运行之前调用的可选函数，每个测试用例都会进行调用

`test`: 带有前缀的函数`test`作为测试用例运行

`testFail`: 前缀的倒数`test`- 如果函数没有恢复，则测试失败



### 6.1.3可见性说明

可见性和solidity语法一样

测试函数必须具有可见`external`性`public`。声明为`internal`或 `private`不会被 Forge 选择的函数，即使它们以`test`.

### 6.1.4进行数据共享

可以定一个合约来进行数据的共享

引入测试库

新建合约，设置全局参数

测试成功环境  带有test前缀的函数作为测试成功用例运行

测试失败环境  带有testFail前缀的函数作为测试失败用例运行，但是最后比值的时候要是 -=

测试失败环境testCannot更好的做法是和一个vm可以造环境的模块一起使用

共享设置，可以通过辅助合约来手机一个共享的参数数据，这个暂时还没看到好的按钮，共享的数据全局进行定义即可



## 6.2 CheatCode

很多情况下，仅仅测试合约输出，查看结果预期往往是不够的，还需要操作区块链的状态。

Foundry可以模拟一个区块链环境，可以进行区块链状态的设置，可以通过vm从Test.sol里面进行调用

### 6.2.1 修改调用对象

下面通过一个案例先了解一下vm的使用方式

```solidity
pragma solidity 0.8.10;

import "forge-std/Test.sol";

error Unauthorized();

contract OwnerUpOnly {
    address public immutable owner;
    uint256 public count;

    constructor() {
        owner = msg.sender;
    }

    function increment() external {
        if (msg.sender != owner) {
            revert Unauthorized();
        }
        count++;
    }
}

contract OwnerUpOnlyTest is Test {
    OwnerUpOnly upOnly;

    function setUp() public {
        upOnly = new OwnerUpOnly();
    }

    function testIncrementAsOwner() public {
        assertEq(upOnly.count(), 0);
        upOnly.increment();
        assertEq(upOnly.count(), 1);
    }
}

```

测试一个设置了管理员权限的合约，我们执行`foege test`可以看到，我们通过部署该合约的地址去调用的话，是可以测试通过的。

我们可以通过vm去修改调用者去模拟失败环境

将测试用改成下面的代码

```solidity
function testIncrementAsOwner() public {
        assertEq(upOnly.count(), 0);
        vm.prank(address(0)); //将调用者换成0地址
        upOnly.increment();
        assertEq(upOnly.count(), 1);
}
```

这个时候我们的测试就会报错，但是一般模拟失败环境测试我们可以用testFail编写测试用例

```solidity
function testFailIncrementAsNotOwner() public {
        vm.prank(address(0));
        upOnly.increment();
}
```

testFail用例则需要遇到revert才会通过测试，但是要去追踪导致revert的原因是否是测试用例需要的失败环境导致

### 6.2.2expectEmit

好像是检查事件参数，没咋看懂



vm可以更改区块链环境，包括修改区块号，调用者等等

vm.prank(address(A))可以修改成调用者为A

-vv可以控制不同的输出

--match-test 测试函数名  可以匹配到具体的测试函数

vm.expectRevert(aaa) 可以模拟revert

vm.expectEmit应该是可以模拟触发事件



## 6.3 标准测试库概览

Forge Standard Library（简称 Forge Std）是一个有用的合约集合，可以让编写测试更简单、更快速、更人性化

它提供了开始编写测试所需的所有基本功能：

- `Vm.sol`: 最新的作弊码界面
- `console.sol`和`console2.sol`：Hardhat 风格的日志记录功能
- `Script.sol`: [Solidity 脚本的基本实用程序](https://book.getfoundry.sh/tutorials/solidity-scripting.html)
- `Test.sol`: DSTest 的超集，包含标准库、作弊码实例 ( `vm`) 和 Hardhat 控制台

只需在您的测试合约中导入`Test.sol`并继承：`Test`，你就可以使用vm、console和console2等方法。

**注意：** `console2.sol`包含`console.sol`允许 Forge 解码控制台调用跟踪

你也可以分开引用这些函数

```solidity
import "forge-std/Vm.sol";
import "forge-std/console.sol";
import "forge-std/console2.sol";
```

### 6.3.1 标准库的组成

Forge Std 目前由六个标准库组成。

* #### [标准日志](https://book.getfoundry.sh/forge/forge-std#std-logs)

* #### [标准断言](https://book.getfoundry.sh/forge/forge-std#std-assertions)

* #### [标准秘籍](https://book.getfoundry.sh/forge/forge-std#std-cheats)

* #### [标准错误](https://book.getfoundry.sh/forge/forge-std#std-errors)

* #### [标准存储](https://book.getfoundry.sh/forge/forge-std#std-storage)

* #### [标准数学](https://book.getfoundry.sh/forge/forge-std#std-math)

更详细的解释等理解更深刻以后补充



## 6.4 [Traces](https://book.getfoundry.sh/forge/traces#understanding-traces)

Foundry可以为所有的测试生成追踪

### 6.4.1 追踪的格式

```
  [<Gas Usage>] <Contract>::<Function>(<Parameters>)
    ├─ [<Gas Usage>] <Contract>::<Function>(<Parameters>)
    │   └─ ← <Return Value>
    └─ ← <Return Value>
```

熟悉写一个测试的demo来分析一下



## 6.5 分叉测试

Forge 支持使用两种不同的方法在分叉环境中进行测试

没看懂



# 7、高级测试

Forge 带有许多高级测试方法：

- [模糊测试](https://book.getfoundry.sh/forge/fuzz-testing.html)
- [不变性测试](https://book.getfoundry.sh/forge/invariant-testing.html)
- [差异测试](https://book.getfoundry.sh/forge/differential-ffi-testing.html)

未来，Forge 还将支持这些：

- [符号执行](https://book.getfoundry.sh/forge/advanced-testing#)
- [变异测试](https://book.getfoundry.sh/forge/advanced-testing#)

## 7.1 [Fuzz Testing](https://book.getfoundry.sh/forge/fuzz-testing#fuzz-testing)

模糊测试就是自动的去尝试参数



## 7.2 不变性测试

貌似是一个预定于一组测试变量，然后进行随机调用，这样可以模拟很多环境状态



不变测试活动有两个维度，`runs`和`depth`：

- `runs`：生成并运行函数调用序列的次数。
- `depth`: 在给定的`run`. 所有定义的不变量在每次函数调用后都被断言。如果函数调用恢复，`depth`计数器仍会递增。

类似于在 Foundry 中通过在函数名称前加上前缀来运行标准测试，不变测试通过在函数名称前加上(例如， )`test`来表示。`invariant``function invariant_A()`



# Cast

主要是去和链进行交互



# anvil 模拟网络环境



