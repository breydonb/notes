# What is Dependency Injection?

Dependency Injection is a way to inject classes into other classes.
## Why Would You Use Dependency Injection

Instead of creating a constructor in a nested class to initialize another object, you can use dependency injection to automatically change references to code.

~~~
public class Person
{
	public Person(string name)
	{
		var logger = new Logger();
		logger.Log($"{name} was created");
	}
}
~~~

In this case, the person class relies on the logger class to be called in the constructor. If we changed any attributes in the constructor, the code wouldn't work.

Instead, you can provide the object into the constructor's arguments to prevent this from being a problem.
~~~
public class Person
{
	public Person(string name, Logger logger)
	{
		logger.Log($"{name} was created");
	}
}
~~~
