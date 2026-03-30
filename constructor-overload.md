# Part 1: Mental model question
## Question 1
Consider the following usage:
```java
User u1 = new User("alice");  
User u2 = new User("bob", "bob@email.com");  
User u3 = new User("charlie", "charlie@email.com", 25);
```

**Questions:**
- What problem is constructor overloading solving in this example?
- What would the alternative designs look like without it?
- What issues might arise with those alternatives?
## Question 2
Given the following class:
```java
class User {  
	String username;  
	String email;  
	int age;  
  
	User(String username) {  
		this.username = username;  
	}  
  
	User(String username, String email) {  
		this.username = username;  
		this.email = email;  
	}  
  
	User(String username, String email, int age) {  
		this.username = username;  
		this.email = email;  
		this.age = age;  
	}  
}
```

**Questions:**
- Will this code compile? Why or why not?
- What makes these constructors different from each other?
- Would this still compile if two constructors had the same parameter types?
## Question 3
Consider the following constructor variations:
```java
User(String username) {}  
User(int age) {}  
User(String name, int age) {}  
User(int age, String name) {}
```

**Questions:**
- Which of these are valid together in the same class?
- What rule determines whether two constructors can coexist?
- Does the order of parameters matter?
## Question 4
Given the following class:
```java
class User {  
	String username;  
	String email;  
  
	User(String username) {  
		this(username, "unknown@email.com");  
	}  
  
	User(String username, String email) {  
		this.username = username;  
		this.email = email;  
	}  
}
```

**Questions:**
- What does `this(...)` do in this context?
- Can a constructor call more than one constructor?

## Question 5:
Consider the following:
```java
User(String username) {  
    System.out.println("Creating user");  
    this(username, "default@email.com");  
}
```

**Questions:**
- Will this compile? Why or why not?
- What rule is being enforced here?

Now consider:
```java
User(String username) {  
    this(username, "default@email.com");  
}
User(String username, String email) {  
    this(username);  
}  
```

**Questions:**
- What happens in this situation?
- Why might this be problematic?

## Question 6
Given:
```java
User(String username) {  
    this.username = username;  
    this.email = "default@email.com";  
}  
  
User(String username, String email) {  
    this.username = username;  
    this.email = email;  
}
```

**Questions:**
- What duplication exists here?
- If validation rules were added, how many places would need to change?
- How would you rewrite the constructor above to reduce duplicates?

# Part 2: Exercises

## Exercise 1
Create a `User` class with:
- username only
- username + email
- username + email + age
## Exercise 2
Refactor your class so that:
- there is one main constructor
- other constructors delegate to it using `this(...)`
## Exercise 3
Add rules:
- username cannot be empty
- age must be >= 0

Ensure:
- all constructors enforce these rules
## Exercise 4
Try to:
- place code before `this(...)`
- create constructors that call each other

Observe and explain:
- what is allowed
- what is prevented
