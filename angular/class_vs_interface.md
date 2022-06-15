# Class vs Interface
---

Here we going to demonstrate the difference between class and interface as used in Angular.

# Definition
---
**Class:** Classes are the basic entities used to create reusable components. Further, it is a group of objects which have common properties. It can contain properties like fields, methods, constructors etc.

```bash 
    export class Product{
        productName: string;
        productCode: number;
    }
```
The export keyword is used to make the class accessible by other modules in our application. Classes are constructed using the class keyword.

**Interface** An interface defines a structure that acts as a contract in an angular application. It only contains methods and fields but not implementation.

```bash
    export interface Product{
        id: number;
        productName: string;
    }
```

# Differences between Class and Interface
---

It it constructed using the keyword interface.

| | Class | Interface |
|------------|-------|-----------|
| **Definition** | A class is the basic entities used to create reusable components| An interface defines a structure that acts as a contract in an angular application.|
| **Creation** | Create using the Keyword *Class* | Create using the keyword *interface* |
| **Access** | Members of a class can be public, protected or private | Members of an interface are always public |
| **Constructor Fucntion** | Classes can have a constructor function | Interface cannot have a constructor function |
| **Usage** | It is used for object creation. encapsulation for fields and methods | It is used to create a structure of an entity |
| **Instantiation** | A class can be instanciated to create an object | An interface cannot be instantiated |