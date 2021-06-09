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
