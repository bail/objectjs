# Object.js

## Classes
```javascript
var MyClass = Object.create({});
```

## Public Properties
```javascript
MyClass.publicProperty = 'value';
```

## Private Properties
```javascript
Object.defineProperty(MyClass, '_privateProperty', { // by convention, starts with underscore 
  value: 'value',
  enumerable: false
});
```

## Inheritance/Extension
```javascript
var Subclass = Object.create(MyClass);
```

## Mixins
```javascript
var mixin = { mixinProperty: 'mixinValue' };
Object.assign(Subclass, mixin);
```
- Mixins can be added to a class at any point during its lifespan, and will retroactively be applied to all existing instances of the class or its subclasses.
- Mixin properties with identical names, on the same class, will override each other, 
## Instantiation
```javascript
var instance = Object.create(Subclass);
```

## Property Introspection
```javascript
Object.getOwnPropertyDescriptor(instance, 'publicProperty');
  // {value: 'value', writable: true, enumerable: true, configurable: true}
```

## Class Introspection
```javascript
Object.getOwnPropertyDescriptors(Subclass);
  // { mixinProperty: { configurable: true, enumerable: true, value: 'mixinValue', writable: true } }
```

## Hierarchy Introspection
```javascript
MyClass.isPrototypeOf(SubClass); // true
```
```javascript
MyClass.hasOwnProperty('publicProperty'); // true
Subclass.hasOwnProperty('publicProperty'); // false
```

