# Backpropogation-Assignment PART 1

**NETWORK EXPLAINED**

**Input neurons**
The current network starts with 2 inputs i1 and i2.

**Applyting Weights on input layer**
The input neuron i1 is mulpilied with weight w1 and i2 multiplied with weight w2. This is passed to the hidden layer and becomes h1.
Likewise i1 is multipled by w3 and i2 with w4. This goes to the hidden layer and acts as h2.

**Hidden Layer activation**
Both h1 and h2 are activated using activation function. Activated neuron becomes out_h1 and out_h2.

**Applying weights on hidden layer**
Fresh weights w5 and w6 are applied on out_h1 and out_h2 respectively. This acts as the predicted output o1. Likewise, w7 and w8 are applied on out_h1 and out_h2 respectively for predicted output o2. 

**Output Activation**
Activation function is applied on both outputs o1 and o2. This becomes out_o1 and out_o2. 

**Error calculation** 
out_o1 and out_o2 is comapred with actual outputs t1 and t2 to arrive at error E1 and E2 respectively. E1 and E2 combined gives us the Total Error "E_Total"

**Backpropogation**
For the backpropogation we trace the Error(E_Total) to the back layers using partial derivatives. This partial derivative is calcualted for the Error with respect to each weight(w1, w2, w3, w4, w5, w6, w7 and w8). 
e.g. partial derivative of E_total w.r.t w5 needs to follow the route of **w5>o1>out_o1>>E1>E_Total**
It is explained as below:
d(E_total)/d(w5)=d(E1+E2)/d(w5)=d(E1+0)/d(w5)=d(E1)/d(out_o1)*d(out_o1)/d(o1)*d(o1)/d(w5)
Each part is calculated and we finally arrive at : **(out_o1-t1)*(out_o1(1-out_o1))*out_h1**
We have arrived at the following derivative functions for each weights:

**w1**- 2 routes are possible. (1)w1>h1>out_h1>w5>o1>out_o1>E1>E_Total.  (2) w1>h1>out_h1>w7>o2>out_o2>E2>E_Total. We have utilized common routes (a) d(E1)/d(Out_h1) and (b) d(E2)/d(Out_h1). The output of these 2 routes are combined and d(out_h1)/d(h1) and d(h1)/d(w1) are added. Hence we get our final output.

w1: **(((out_o1-t1)*out_o1*(1-out_o1)*w5)+((out_o2-t2)*out_o2*(1-out_o2)*w7))*out_h1(1-out_h1)*i1**

**w2**- E_Total w.r.t. w2 follows the same route as w1 except the inital weight of w2. Hence we take the entire equation and just multiply by i2 at the end instead of i1

w2: **(((out_o1-t1)*out_o1*(1-out_o1)*w5)+((out_o2-t2)*out_o2*(1-out_o2)*w7))*out_h1(1-out_h1)*i2**

**w3**- E_Total w.r.t. w2 starts from w3>h2>out_h2> and then follows 2 routes (a)w6>o1_out_o1>E1>E_Total (b)w8>o2>out_o2>E2>E_Total. The whole route is worked out and we get the below:

w3: **((out_o1-t1)*out_o1*(1-out_o1)*w6)+((out_o2-t2)*out_o2*(1-out_o2)*w8))*Out_h2(1-Out_h2)*i1**

**w4**-This follows the same route as w3 except the beginning weight of w3. Here we the take same equation of w3 and multiply by i2 at the end instead of i1.

w4: **((out_o1-t1)*out_o1*(1-out_o1)*w6)+((out_o2-t2)*out_o2*(1-out_o2)*w8))*Out_h2(1-Out_h2)*i2**

**w5**- This is already explained at the beginning

**w6**-This follows the same route as w5 except the starting weight of w6 instead of w5. Hence we take the same equation and multiply by out_h2 instead of out_h1 at the end.

w6: **(out_o1-t1)*(out_o1(1-out_o1))*out_h2**

**w7**-This follows the route of w7>o2>out_o2>E2>E_Total.

w7: **(out_o2-t2)*out_o2(1-out_o2)*out_h1**

**w8**-This follows the same route as w7 except the beginning weight of w8. Hence we take w7's equation and multiply by out_h2 instead of out_h1 at the end.

w8: **(out_o2-t2)*out_o2(1-out_o2)*out_h2**

The derivative we get out of this process is used to update the weights with the help of learning rate.

**Updating weights with learning rate**
To update w1, the formula used is w1-learning rate*((partial derivtive of E_Total) w.r.t. partial derivative of w1). Rest of the weigts follow.

<img width="925" alt="Backpropogation3" src="https://user-images.githubusercontent.com/90223404/137605787-a03d358c-2b3f-40ee-aefb-f8a06fdf45d6.png">


**Changing the learning rate**
learning rate at 0.1:-  
<img width="279" alt="LR 0 1" src="https://user-images.githubusercontent.com/90223404/137605835-51fa82e2-2b85-4d7f-9a0d-d84f593f0a11.png">


learning rate at 0.2:-
<img width="268" alt="LR 0 2" src="https://user-images.githubusercontent.com/90223404/137605854-82ee08c0-1c2e-4411-a26b-448ca4e77ab0.png">


learning rate at 0.5:-
<img width="268" alt="LR 0 5" src="https://user-images.githubusercontent.com/90223404/137605903-5be2854d-5fc5-4974-82a3-4dfd9d941919.png">



learning rate at 0.8:-
<img width="267" alt="LR 0 8" src="https://user-images.githubusercontent.com/90223404/137605947-9576631a-9a2b-44db-bff3-01279d65a3f1.png">



learning rate at 1.0:-
<img width="268" alt="LR 1 0" src="https://user-images.githubusercontent.com/90223404/137605971-94a48520-8cd9-49b8-9fdd-0d4b31868bc4.png">



learning rate at 2.0:-
<img width="269" alt="LR 2 0" src="https://user-images.githubusercontent.com/90223404/137606005-027c2136-11be-4a4c-810f-2e21a1ea58f8.png">



