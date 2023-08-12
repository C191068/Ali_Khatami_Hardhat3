![image](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/0ee53c7a-c9b1-4559-9ff2-74a207814039)# Ali_Khatami_Hardhat3(Learning from the video of Pattrick Collins)
### Mocking

Mocking is primarily used for unit testing. In simple words mocking is creating objects that simulate the behavior of real objects <br>

When going for localhost or hardhat network we are going to use mock <br>

![h29](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/17478dc9-5307-4399-9e42-621d0c105a98)
Figure1: here if we go to this price feed shown with black arrow, we can see ton of different blockchains <br>
each with price feeds shown with blu arrow <br>

The address of Eth/USD of Ethereum is totally different from Eth/USD of Sepolia <br>

![h30](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/f73ec364-337f-4eb1-8439-2fa67987359f)

Figure2: we also need to modularize or parameterize the address shown with yellow arrow shown above <br>

So that no matter what blockchain we deploy to <br>

we don't have to change our code <br>

Now we have to do refractoring of our akrkFundMe.sol code <br>

Refractoring means going back and changing the way your code works <br>

![h31](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/a4444205-9dfd-408b-8f3c-610c302f3eff)

Figure3: here we pass ```address priceFeed``` as a parameter to the above ```constructor``` function shown with yellow arrow<br>


![h32](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/3183e294-ba6e-4302-9ba5-c872d2526095)

Figure4: When we deploy our contract we gonna we gonna pass the Eth/USD price feed address depending <br>
on the network we are using <br>

Now as our constructor takes price feed address as a parameter we gonna save our AggregatorV3Interface as global variable <br>


![h33](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/2d876b1b-dcbf-4b5c-90f8-cd8dd67821e9)

here in this file we create a price feed variable of type AggregatorV3Interface <br>

which we are importing from chainlink repo like below <br>

```import "@chainlink/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol"``` <br>

which is an interface object that gets pop down to ABI <br>




