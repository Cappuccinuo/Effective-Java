Chapter 2 Creating and Destroying Objects

Item1: Consider static factory methods instead of constructors

e.g. Boolean.valueOf

public static Boolean valueOf(boolean b) {
  return b ? Boolean.TRUE : Boolean.FALSE;
}

Advantage:
1. Static factory methods have names. Like BigInteger.probablePrime
2. Static factory methods are not required to create a new object each time they
are invoked.
3. Static factory methods can return an object of any subtype of their return
type.
4. The class of the returned object can vary from call to call as a function of
the input parameters.
5. The class of the returned object need not exist when the class containing
the method is written.
Service Provider Framework: A system in which providers implement a service,
and the system makes the implementations available to clients, decoupling the
clients from the implementations.
e.g. Java Database Connectivity API(JDBC).
Three essential components in a service provider framework:
service interface
provider registration API
service access API (May allow clients to specify criteria for choosing implementations.
Flexible static factory form the basis of service provider frameworks)
(Optional)Service provider interface

For JDBC:
Connection -> service interface
DriverManager.registerDriver -> provider registration API
DriverManager.getConnection -> service access API
Driver -> service provider interface

Disadvantage:
1. Main limitation of providing only static factory methods is that classes
without public or protected constructors cannot be subclassed.
e.g. It is impossible to subclass any of the convenience implementation classes
in the Collections Framework.
2. Static factory methods are hard for programmers to find.
