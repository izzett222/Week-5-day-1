# Part 1: Mental model
## Question 1:
Given:
```java
record User(String username, String email, int age) {}
```

**Questions:**
- Without adding anything else, what methods can you call on a `User` instance?
- How do you access `username`, `email`, and `age`?
- What would this look like if written as a normal class?

## Question 2
Consider:
```java
record User(String username, String email, int age) {  
  
    User {  
        if (username == null || username.isEmpty()) {  
            throw new IllegalArgumentException("Invalid username");  
        }  
    }  
}

```

**Questions:**
- This constructor has no parameter list. what inputs is it receiving?
- Where are the fields actually being assigned?
- What happens if you try to assign `this.username = username;` inside this block?

Now consider:
```java
record User(String username, String email, int age) {  
    User(String username) {  
        this(username, "unknown@email.com", 0);  
    }  
}
```

**Questions:**
- Is this valid?
- How is this constructor different from the previous one?
- What rules must be followed when calling `this(...)` here?
## Question 3
Given:
```java
record User(String username, String email) {   
	public String username() {  
		return username.toUpperCase();  
	}  
}
```

**Questions:**
- What method is being overridden here?
- What will `user.username()` return now?
- Is the underlying value actually changed?

## Question 4
Consider:
```java
record User(String username, String email) {  
  
    void updateEmail(String newEmail) {  
        this.email = newEmail;  
    }  
}
```

**Questions:**
- Will this compile?
- What does this tell you about how record fields behave?
- If you need a “modified” version of a record, what are your options?

Now consider:
```java
record User(String username, String email) {  
    String extra;  
}
```

**Questions:**
- Is adding this field allowed?
- What does this reveal about what a record can and cannot contain?
## Question 5
Consider:
```java
record User(String username) {}  
  
class Admin extends User {}
```

**Questions:**
- Will this compile?
- What does this tell you about inheritance with records?
- Can a record extend another class?


# Part 2: Exercises
## Exercise 1
Create a `User` record with:
- String username
- String email
- int age

Test:
- printing it
- access fields

## Exercise 2
Add validation:
- username cannot be empty
- age must be >= 0
## Exercise 3
Add another way to create a `User`:
- only username provided
- default values for others
## Exercise 4
Modify the record so that:
- `username()` always returns uppercase
Verify:
- original value vs returned value
