# [DesignPattern](https://github.com/pikachu987/SwiftGrammar/tree/master/DesignPattern "SwiftGrammar")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftGrammar)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftGrammar/stargazers)

### 데코레이트 패턴(DecoratorPattern)

````Swift
import UIKit
import UIKit

// Component
// + operation()
protocol Bread {
    func price() -> Int
    func name() -> String
}

// ConcreateComponent
// + operation()
class Pizza: Bread {
    func price() -> Int {
        return 10000
    }
    func name() -> String {
        return "피자"
    }
}

// Decorator
// - component
// + operation()
class PizzaDecorator: Bread {
    let decoratedBread: Bread
    required init(_ decoratedBread: Bread) {
        self.decoratedBread = decoratedBread
    }
    func price() -> Int {
        return self.decoratedBread.price()
    }
    func name() -> String {
        return self.decoratedBread.name()
    }
}

// ConcreateDecorator
// + operation()
class BulgogiPizza: PizzaDecorator {
    required init(_ decoratedBread: Bread) {
        super.init(decoratedBread)
    }
    override func price() -> Int {
        return super.price() + 5000
    }
    override func name() -> String {
        return "불고기 " + super.name()
    }
}

// ConcreateDecorator
// + operation()
class Cheese: PizzaDecorator {
    let cheeseType: String
    required init(_ decoratedBread: Bread, cheeseType: String) {
        self.cheeseType = cheeseType
        super.init(decoratedBread)
    }

    required init(_ decoratedBread: Bread) {
        self.cheeseType = ""
        super.init(decoratedBread)
    }
    override func price() -> Int {
        return super.price() + 2000
    }
    override func name() -> String {
        return self.cheeseType + "치즈 " + super.name()
    }
}

let pizza = Pizza()
print("\(pizza.name())의 가격은 \(pizza.price())")

let bulgogiPizza = BulgogiPizza(pizza)
print("\(bulgogiPizza.name())의 가격은 \(bulgogiPizza.price())")

let cheese = Cheese(bulgogiPizza, cheeseType: "리코타")
print("\(cheese.name())의 가격은 \(cheese.price())")
````

````Swift
피자의 가격은 10000
불고기 피자의 가격은 15000
리코타치즈 불고기 피자의 가격은 17000
````
