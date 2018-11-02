# 初识测试

## assert
断言（assert）表示为一些结果为真或者假的布尔表达式，目的是验证程序开发者预期的结果。

在软件工程中，用错误处理代码来处理预期发生的错误，用断言来处理绝对不应该发生的状况；换句话说开发者可以用断言来检测程序的bug；

前端中的断言：`console.assert()`方法。

NodeJs提供了[Assert模块](http://nodejs.cn/api/assert.html)，该模块可以做一些简单的断言测试。因为Assert模块比较简单，在实际项目中通常使用功能更加完善的断言库；比如`should.js`。


## should.js
一个与测试框架无关的、表现力强且易读、BDD风格的断言库。

在shouldjs之前，先了解一下，BDD是什么。
说到BDD（behavior-driven development），不得不提ATDD（Acceptance test–driven development）和TDD（Test-driven development）， 虽然三者不完全是一个层面的东西，但也有很多的关系；
**验收测试驱动开发（ATTD）**，更像是一种开发方法论，强调需求，测试和开发的协作，要求大家对产品需求都很了解；ATDD包含验收测试，但在开发人员开始编码之前强调编写验收测试（writing acceptance tests， 不知道是不是这么翻译）。

**测试驱动开发（TDD）** 是一种软件开发过程中的实践， 其倡导先写测试程序，然后编码实现其功能。测试驱动开发的目的是通过测试-编程-重构的短周期取得快速反馈。有人认为TDD是代码级别的实践，针对与模块和方法进行的单元测试。

**行为驱动开发(BDD)** 融合了ATTD和TDD的一种开发实践，它要求先写测试，对方法和模块进行单元测试的同时也要求，也关注于对产品行为的描述（行为描述的测试可以由非开发人员编写）。


回过头来看看should.js：
1.  断言链
    每个断言都返回一个可被链接的对象；可以像下面这样调用：

    ```javascript
    user.should.be.an.instanceOf(Object).and.have.property('name', 'tj');
    ```

2. .ok
    js中的真值断言（非 null, undefined, 0 , NaN）
    
    ```
    true.should.be.ok;
    ```
3. .true
    断言 === true

3. .false
    断言 ===false

4. eql(otherValue)
    一个值等于另一个值，注意，**引用类型判断的不是指相同的引用**。

    ```javascript
    // see next example it is correct, even if it is different types, but actual content the same
    [1, 2, 3].should.eql({ '0': 1, '1': 2, '2': 3 });
    ```
5. .equal(otherValue) and .exactly(otherValue)
    断言 === ， 与上一个方法有明显区别。

还有其他断言，需要的时候看看。。。

有了断言库能写测试脚本了， 可是没有如何运行测试脚本呢；用到了测试框架： 比如： mocha；


## mocha

mocha是JavaScript的一种单元测试框架，既可以在浏览器环境下运行，也可以在Node.js环境下运行。

使用mocha，我们就只需要专注于编写单元测试本身，然后，让mocha去自动运行所有的测试，并给出测试结果。

mocha的特点主要有：

- 既可以测试简单的JavaScript函数，又可以测试异步代码，因为异步是JavaScript的特性之一；

- 可以自动运行所有测试，也可以只运行特定的测试；

- 可以支持before、after、beforeEach和afterEach来编写初始化代码。


## Karma
Karma是一个基于Node.js的JavaScript测试执行过程管理工具（Test Runner）,能让你的代码在浏览器环境下测试。需要它的原因在于，你的代码可能是设计在浏览器端执行的，在node环境下测试可能有些bug暴露不出来；
如果你的代码只会运行在node端，那么你不需要用karma。


## CI
### 概念
持续集成服务（Continuous Integration）， 一种软件开发实践，也是软件开发中很重要的一环。CI不是在项目发布前再进行集成，而是只要有新代码提交到仓库中就应该进行集成,在实际项目中通常会自动触发；CI的目的是持续地交付功能可用的软件；

### 常用工具
- jenkins
- travis

### Travis CI
[Travis CI](https://travis-ci.org/)，提供了支持多种编程语言的持续集成服务， 绑定GigHub（不支持其他代码托管服务）项目后，只要有新的代码，就会自动抓取。然后，提供一个运行环境，执行测试，完成构建，还能部署到服务器。

配置文件是项目根目录下的`.travis.yml`，很多开源项目都有，比如[vux](https://github.com/airyland/vux)， [axios](https://github.com/axios/axios);



## 参考：
- [持续集成服务 Travis CI 教程](http://www.ruanyifeng.com/blog/2017/12/travis_ci_tutorial.html)
- 《新时期的Node.js》
- 《代码大全 第2版》
- [测试框架 Mocha 实例教程
](http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html)
- [mocha - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00147203593334596b366f3fe0b409fbc30ad81a0a91c4a000)
