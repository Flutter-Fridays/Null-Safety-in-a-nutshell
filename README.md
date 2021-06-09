# Null-Safety-in-a-nutshell

Dart was originally an unsound optional type system with a sound static type system, but now it's null safety-- meaning that it's required to specified if the value can be null or shouldn't be null at the time of initializing. 

## Example of errors with static type system.
// Without null safety:
bool isEmpty(String string) {
  if (string.length == 0){
    return true;
  }
  return false;
} 
main() {
  isEmpty(null);
}

This code throws a NoSuchMethodError exception on the call to .length since the complier assumes that you tried to call the .length from Null class.

## Ok, I got it, but what's the solution?

We can solve this problem by checking in the first place if the value is null using if else clause.
We can do something like this

bool isEmpty(String string) {
  if (string != null){
    if (string.length == 0){
      return true;
    }
    return false;
  }
  else{
    throw Exception();
  }
    
  return false;
} 
main() {
  isEmpty(null);
}

## Well, that could solve the problem but it's a little hectic isn't it. 
## Are they any better ways?
Yes, introduing the ? symbol.
Just put it after the type declaration and it should solve the problem.
Now our code would look like this.

bool isEmpty(String? string) {
  if (string.length == 0){
    return true;
  }
  return false;
} 
main() {
  isEmpty(null);
}

### Wow, that's very easy. Is there anything else?
Yes, and we must use the ! (Assertion operator) in some cases to confirm that our variable is safe and not null. And we must do that at the time of calling.
main() {
  isEmpty('Hello'!);
}

Note that applying the assertion operator to a null value will throw a runtime exception.



