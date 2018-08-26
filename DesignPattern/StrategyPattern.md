# [DesignPattern](https://github.com/pikachu987/SwiftGrammar/tree/master/DesignPattern "SwiftGrammar")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftGrammar)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftGrammar/stargazers)

### 스트래티지 패턴(StrategyPattern)

````Swift
import UIKit

protocol Strategy {
    func doOperation(_ num1: Int, _ num2: Int) -> Int
}

class OperationAdd: Strategy {
    func doOperation(_ num1: Int, _ num2: Int) -> Int {
        return num1 + num2
    }
}

class OperationSubtract: Strategy{
    func doOperation(_ num1: Int, _ num2: Int) -> Int {
        return num1 - num2
    }
}

class OperationMultiply: Strategy{
    func doOperation(_ num1: Int, _ num2: Int) -> Int {
        return num1 * num2
    }
}

class Context{
    let strategy: Strategy
    init(strategy: Strategy) {
        self.strategy = strategy
    }
    func execute(_ num1: Int, _ num2: Int) -> Int{
        return self.strategy.doOperation(num1, num2)
    }
}


let contextAdd = Context(strategy: OperationAdd())
print(contextAdd.execute(10, 20))

let contextMultiply = Context(strategy: OperationMultiply())
print(contextMultiply.execute(20, 2))
````

````Swift
30
40
````
