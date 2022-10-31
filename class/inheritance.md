- [1. access specifier](#1-access-specifier)
  - [1.1. type of members](#11-type-of-members)
  - [1.2. type of inheritance](#12-type-of-inheritance)
- [2. constructors and destructors' call](#2-constructors-and-destructors-call)
- [3. mutltiple inheritance](#3-mutltiple-inheritance)

**Derived class** inherits **Base class**.

A derived class inherits all base class methods with the following exceptions:

- Constructors, destructors
- Overloaded operators
- The friend functions

# 1. access specifier

## 1.1. type of members

If no access specifier is defined, all members of a class are set to `private` by default.

3 types of member:

- `public`:
  objects can directly call memebers; derived class can inherit members.
- `protected`
  objects cannot directly call memebers; derived class can inherit members.
- `private`
  both not.

## 1.2. type of inheritance

If no access specifier is used when inheriting classes, the type becomes `private` by default.

3 types of inheritance:

- `public` Inheritance:
  public -> public, protected -> proteced, private invisible.
  But private members can be accessed through calls to the public and protected functions of the base class.
- `protected` Inheritance:
  public, protected -> protected
- `private` Inheritance:
  public, protected -> private

# 2. constructors and destructors' call

When inheriting classes, the base class' constructor and destructor are not inherited. However, they are being called when an object of the derived class is created or deleted.

1. base class's constructor -> derived class's constructor
2. derived class's destructor -> base class's destructor

# 3. mutltiple inheritance

A class can be derived from multiple classes by specifying the base classes in a comma-separated list. For example:

`class Daughter: public Mother, public Father`.
