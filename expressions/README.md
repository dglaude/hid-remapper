Trying various usage of expressions to computer/filter mouse movement based on mouse input.

Warning, make sure you have `Unmapped inputs passthrough on layer` on all layer so that active or not mouse click continue to work. Like this:

<img width="538" alt="warning" src="https://user-images.githubusercontent.com/19435932/236567800-e5f8dab8-770d-46e5-a479-0612eb530dcc.PNG">

**Test 1: Clipping X and Y values**

This could have some usefullness for filtering Tremor as it limit big movement to the maximum value. This also slow down any fast movement you may want to do.

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

This is totally useless for any kind of Tremor, it offer no added value that the official "rotate mouse by 30 degrees" from the example page on https://www.jfedor.org/hid-remapper-config/ but is just another way to implement the same thing.

Here are the two expressions to use:
* `0x00010030 input_state 0.866 mul 0x00010031 input_state 0.5 mul add` <= Compute new X based on old x and y
* `0x00010030 input_state -0.5 mul 0x00010031 input_state 0.866 mul add` <= Compute new Y based on old x and y

This is what it should look like in the UI side:

<img width="535" alt="02_30°rotation_mapping" src="https://user-images.githubusercontent.com/19435932/236522246-2558fd29-41d6-400f-b869-f2763584d173.PNG">
<img width="537" alt="02_30°rotation_expressions" src="https://user-images.githubusercontent.com/19435932/236522271-2e6ca5ea-1cd9-432b-805c-a62f79503a49.PNG">

The easy way to configure that is to use the examples: "expressions: middle button enables mouse jiggler"

And modify the two expressions.

Else you have to use the json export and import that.

**Test 2b: Rotate any° using expressions**

This is totally useless for any kind of Tremor.
It is just the generalisation of the official "rotate mouse by 30 degrees" from the example page on https://www.jfedor.org/hid-remapper-config/ but this time you have to define the same angle *twice* in the `Scaling` box of the mapping. Default value in the json file is 30° but you can change that.

Here are the two expressions to use:
* `0x00010030 input_state scaling cos mul 0x00010031 input_state scaling sin mul add` <= Compute new X based on old x and y
* `0x00010030 input_state scaling sin -1 mul mul 0x00010031 input_state scaling cos mul add` <= Compute new Y based on old x and y

This is what it should look like in the UI side (imporant point, you need to put twice the angle in degree in the Scaling box for both X and Y computation):

<img width="534" alt="02b_30°rotation_mapping" src="https://user-images.githubusercontent.com/19435932/236534605-00bbe314-6980-4e9c-859f-3f73a2324b9c.PNG">
<img width="540" alt="02b_30°rotation_expressions" src="https://user-images.githubusercontent.com/19435932/236534622-cb054d7f-2812-4a6d-bb40-68a28268dad4.PNG">

The easy way to configure that is to use the examples: "expressions: middle button enables mouse jiggler"

And modify the two expressions, and the scaling value.

Else you have to use the json export and import that.

