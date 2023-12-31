# Ali_Khatami_Hardhat3(Learning from the video of Pattrick Collins)
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

if we match an ABI up with an address we get a contract thet we can interact with <br>

![h34](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/a62db684-c999-4605-890b-10e255c2d546)

Here above we made the changes in the code <br>

Now we have priceFeed address i.e is modularized and variable depending on the chain we are working <br>

Now we can use this priceFeed address and use it for our akrkPriceConvertor library <br>

![h35](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/d118e2bb-969e-4760-b1ed-ef0e32295987)

We are using akrkPriceConvertor library for uint256 <br>

We are using it as a library on top olf our uint256 <br>

![h33](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/f41a453e-b027-4590-9a6a-7c8a3718bfd7)

We are calling ```msg.value.getConversionRate()``` at akrkFundMe.sol file <br>

![h37](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/8f76a7c2-9923-4abe-afc8-eaee0d868b58)

Now we look at ```akrkPriceConvertor.sol``` we have ```function getConversionRate( uint256 ethAmount)```  <br>

which takes uint256 ethAmount as initialize parameter <br>

![h38](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/4f9f1dad-a5fe-41dc-a4b7-f253740f7a34)


which again since it is a library it automatically passes ```msg.value``` into this ```getConversion()``` <br>
function <br>


![h39](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/7cf9d455-122e-452c-8b3b-60091ed0be7b)

We can also pass in this priceFeed <br>

![h40](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/4dd76241-b582-4d86-a9b3-0bce8fffa07a)

And then we don't need to hard code at ```getPrice()``` function anymore <br>

![h41](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/a43e635a-309f-4623-8304-000485532e28)

Here initial parameter gonna be msg.value and second parameter gonna be priceFeed <br>


A quick refresher <br>

![h42](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/2bc9ba5b-22a1-4402-b204-ba5062dfee5d)

We are parametrizing the priceFeed address shown with yellow arrow and passing it with constructor <br>

![h43](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/408b500e-0e30-44d1-a69f-1c94b4c601da)

Then we save it as a global variable of AggregatorV3Interface type <br>

![h44](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/00a7a1c0-dedf-41e8-9c2e-9ce9abfcc7f4)

Then we are passing it to getConversionRate() function <br>

![h45](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/1d346647-323e-4045-ab6e-98c9b8c3dced)

which passes it getprice() function <br>

![h46](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/b07ab90a-d9b3-4438-b51b-27b8ce607c84)

which then just calls the latestRoundData() <br>

Thus we have done the refractoring <br>

![h47](https://github.com/C191068/Ali_Khatami_Hardhat3/assets/89090776/4c9e44e0-b063-4c74-a230-0bb3474b8655)

To compile we give the command ```yarn hardhat compile``` and it ius successfully compiled <br>

We have just refactored our code now we can price feed address depending on the network we are <br>




