# GumballMachineTestDrive-withoutstate

Comparison Between Using State Pattern and Without State Pattern

1. Difference in Output Behavior
One key difference I noticed is how the output is produced when using the State Design Pattern.
In the State version, the machine calls:

state.dispense();

every time turnCrank() is executed.

So, if the current state is SoldOutState and the user turns the crank, the output becomes:

You turned, but there are no gumballs
No gumball dispensed

However, in the version without the State Pattern, the output is only:

You turned, but there are no gumballs

This is because the non-state version does not trigger a separate dispense() call for every crank turn.

2. Adding or Transitioning Between States
Another observation is that the process of adding a new state or transitioning between states is not dramatically different between the two implementations.

Both versions require:
- Checking the current state
- Deciding the next state
- Updating behavior based on conditions

The difference becomes more significant only when the number of transitions grows and you want to add a new state.

3. Ease of Modification
The advantage of the State Pattern becomes clear when the machine has many transitions.

Then the State Pattern is the better choice, because modifying behavior in a large if/else system becomes difficult and error-prone.

When NOT to Use the State Pattern
If:
- The number of transitions is small


Then a simple implementation without the State Pattern is acceptable and easier to maintain.


Note:
I found the version of the code without the State Pattern in the same project.
The changes I made were:

1-Inside the private void dispense() method, I deleted the following code:

} else if (state == NO_QUARTER) {
    System.out.println("You need to pay first");
} else if (state == SOLD_OUT) {
    System.out.println("No gumball dispensed");
} else if (state == HAS_QUARTER) {
    System.out.println("No gumball dispensed");
}


2-I compared the State pattern with the version without State.
