Trying various usage of expressions to filter tremor mouvement on the mouse input.

**Test 1: Clipping X and Y values**

Here are the two expressions to use:
* `0x00010030 input_state scaling -1 mul scaling clamp` <= Filter X value
* `0x00010031 input_state scaling -1 mul scaling clamp` <= Filter Y value

This is what it should look like in the UI side:

<img width="543" alt="01_clipping_mapping" src="https://user-images.githubusercontent.com/19435932/236273393-416bdc4d-5413-4be6-becc-58c75de83e8f.PNG">
<img width="539" alt="01_clipping_expressions" src="https://user-images.githubusercontent.com/19435932/236273424-1538dc0f-8918-4be2-9c92-d3b59262aca7.PNG">

The easy way to configure that is to use the examples: "expressions: middle button enables mouse jiggler"

And modify the two expressions.

Else you have to use the json export and import that.

**Test 2: Rotate 30° using expressions**

Here are the two expressions to use:
* `0x00010030 input_state 0.866 mul 0x00010031 input_state 0.5 mul add` <= Compute new X based on old x and y
* `0x00010030 input_state -0.5 mul 0x00010031 input_state 0.866 mul add` <= Compute new Y based on old x and y

This is what it should look like in the UI side:

<img width="535" alt="02_30°rotation_mapping" src="https://user-images.githubusercontent.com/19435932/236522246-2558fd29-41d6-400f-b869-f2763584d173.PNG">
<img width="537" alt="02_30°rotation_expressions" src="https://user-images.githubusercontent.com/19435932/236522271-2e6ca5ea-1cd9-432b-805c-a62f79503a49.PNG">

The easy way to configure that is to use the examples: "expressions: middle button enables mouse jiggler"

And modify the two expressions.

Else you have to use the json export and import that.
