```
import Foundation

class Parent {
    var parentProperty: String
    
    init(parentProperty: String) {
        self.parentProperty = parentProperty
    }
    
    func parentMethod() {
        print("This is a method of Parent class")
    }
}

class Child1: Parent {
    var child1Property: Int
    
    init(parentProperty: String, child1Property: Int) {
        self.child1Property = child1Property
        super.init(parentProperty: parentProperty)
    }
    
    override func parentMethod() {
        super.parentMethod()
        print("This is a method overridden by Child1")
    }
}

class Child2: Parent {
    var child2Property: Double
    
    init(parentProperty: String, child2Property: Double) {
        self.child2Property = child2Property
        super.init(parentProperty: parentProperty)
    }
    
    override func parentMethod() {
        super.parentMethod()
        print("This is a method overridden by Child2")
    }
}

class House {
    var width: Double
    var height: Double
    
    init(width: Double, height: Double) {
        self.width = width
        self.height = height
    }
    
    func create() {
        print("House created. Area: \(width * height)")
    }
    
    func destroy() {
        print("House destroyed.")
    }
}

/*   Отличия между структурами и классами:

Структуры и классы являются основными строительными блоками в Swift. Они могут содержать свойства и методы для описания определенных сущностей или объектов. Однако есть несколько ключевых различий между ними:

    Наследование: Классы поддерживают наследование, тогда как структуры этого не поддерживают.
    Ссылочный тип и значимый тип: Классы являются ссылочными типами, что означает, что при присваивании экземпляра класса переменной или передаче его в качестве аргумента функции, передается ссылка на тот же экземпляр. Структуры, напротив, являются значимыми типами, что означает, что они копируются при присваивании или передаче в функцию.
    Инициализаторы: Классы могут иметь дополнительные инициализаторы и наследовать инициализаторы от своих суперклассов. Структуры автоматически получают инициализаторы от Swift.
    Неизменяемость: Экземпляры структур являются неизменяемыми (immutable) по умолчанию, если они объявлены как константы (let). Это означает, что их свойства не могут быть изменены после создания экземпляра. Классы не имеют такого свойства неизменяемости по умолчанию.
    */
struct Student {
    var name: String
    var age: Int
}

class PokerGame {
    var deck: [String] = []
    
    init() {
        let suits = ["♥️", "♦️", "♣️", "♠️"]
        let ranks = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"]
        
        for suit in suits {
            for rank in ranks {
                deck.append("\(rank)\(suit)")
            }
        }
    }
    
    func dealHand() -> [String] {
        var hand: [String] = []
        
        for _ in 1...5 {
            if let card = deck.randomElement() {
                hand.append(card)
                if let index = deck.firstIndex(of: card) {
                    deck.remove(at: index)
                }
            }
        }
        return hand
    }
}

func evaluateHand(hand: [String]) -> String {
    // как-то оно определяет
    return "У вас не флеш"
}

// Пример использования классов и функций
let parentObject = Parent(parentProperty: "Parent Property")
parentObject.parentMethod()

let child1Object = Child1(parentProperty: "Parent Property", child1Property: 10)
child1Object.parentMethod()

let child2Object = Child2(parentProperty: "Parent Property", child2Property: 3.14)
child2Object.parentMethod()

let house = House(width: 10.0, height: 5.0)
house.create()
house.destroy()

let students = [
    Student(name: "Alice", age: 20),
    Student(name: "Bob", age: 25),
    Student(name: "Charlie", age: 22)
]

let pokerGame = PokerGame()
let hand = pokerGame.dealHand()
let combination = evaluateHand(hand: hand)
print("Your combination: \(combination)")

```

![изображение](https://github.com/vihuhool/swifty4/assets/69204363/74afc96c-dcff-42f7-a00e-a583cd7096e8)
