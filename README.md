# 2020-1-1-VSCodeExtentionSmartContracts

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Event URL: [https://bit.ly/34P1MJJ./](https://bit.ly/34P1MJJ)

# An introduction to the IBM Blockchain Platform 2.0!

# Contacts:

## Linkedin.com/in/lennartfrantzell/
 
<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

[Whitelisting](https://cloud.ibm.com/registration/whitelist)

# Sources

<a href="https://hyperledger-fabric.readthedocs.io/en/release-1.4/">Hyperledger Fabric Read the Docs</a>

<a href="https://github.com/hyperledger/fabric">Hyperledger Fabric source code on GitHub</a>
 

# I) Learning Objectives:

What we will be doing:

## 1. Sign up to a free IBM Cloud account
 
 Why will we sign up to a free IBM Cloud account?
 Because IBM Blockchain Platform runs in the IBM cloud.
 
[https://ibm.biz/BdzSJN](https://ibm.biz/BdzSJN)

<img src="img/login.png">
 
## 2. Install Visual Studio Code


[Click on link to install Visual Studio Code](https://code.visualstudio.com)
<p>
<img src="img/vsc.png">

Why will we install Visual Studio Code?
 Because it comes with a Plugin-in for the IBM Blockchain Platform, which makes it easy to create Smart Contracts.

[Complete instructions: Install IBM Blockchain Platform VS Code extension for free](http://cloud.ibm.com/docs/services/blockchain?topic=blockchain-develop-vscode#develop-vscode-install)


## 3. Install IBM Blockchain Platform Plugin in Visual Studio Code

<img src="img/marketplace.png">

[Click on link to install IBM Blockchain Platform Plugin in Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=IBMBlockchain.ibm-blockchain-platform) 
 
### Please Note: Install issues documented at: https://github.com/IBM-Blockchain/blockchain-vscode-extension/issues/
 
## 4. Launch IBM Blockchain Platform in the IBM Cloud

<img src="/img/ibm.blockchain.platform.png">

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

 
 # II) Developing Smart Contracts in VSCode
 
 <img src="img/tutstart.png">
 
 
 ## 2 Understading the Smart Contract
 
 
The generated smart contract code scaffold provides a good example of some common operations for interacting with data on a blockchain ledger. If you're in a big rush, you could skip this section, but why not stay a while and listen as we learn the basic anatomy of a smart contract!


Notice the lines that start with @Transaction - these are functions that define your contract's transactions i.e. the things it allows you to do to interact with the ledger.


Skipping over the first one (myAssetExists), take a look at the createMyAsset function:
 
 ### Typescript 1
 
 ```
    @Transaction()
    public async createMyAsset(ctx: Context, myAssetId: string, value: string): Promise<void> {
        const exists = await this.myAssetExists(ctx, myAssetId);
        if (exists) {
            throw new Error(`The my asset ${myAssetId} already exists`);
        }
        const myAsset = new MyAsset();
        myAsset.value = value;
        const buffer = Buffer.from(JSON.stringify(myAsset));
        await ctx.stub.putState(myAssetId, buffer);
    }
 ```
 ### Java 1
 
 ```
 @Transaction()
    public void createMyAsset(String myAssetId, String value) {
        Context ctx = getContext();
        boolean exists = myAssetExists(myAssetId);
        if (exists) {
            throw new RuntimeException("The asset "+myAssetId+" already exists");
        }
        MyAsset asset = new MyAsset();
        asset.setValue(value);
        ctx.putState(myAssetId, asset.toJSONString().getBytes(UTF_8));
    }
 
 ```

The empty brackets in @Transaction() tells us that this function is intended to change the contents of the ledger. Transactions like this are typically submitted (as opposed to evaluated) - more on that later in this tutorial! The function is called createMyAsset and it takes myAssetId and a value, both of which are strings. When this transaction is submitted, a new asset will be created, with key myAssetId and value value. For example if we were to create "001", "A juicy delicious pineapple", then when we later read the value of key 001, we'll learn the value of that particular state is A juicy delicious pineapple.

Now, take a look at the next transaction:

### Typescript 2


 ```
 
  @Transaction(false)
    @Returns('MyAsset')
    public async readMyAsset(ctx: Context, myAssetId: string): Promise<MyAsset> {
        const exists = await this.myAssetExists(ctx, myAssetId);
        if (!exists) {
            throw new Error(`The my asset ${myAssetId} does not exist`);
        }
        const buffer = await ctx.stub.getState(myAssetId);
        const myAsset = JSON.parse(buffer.toString()) as MyAsset;
        return myAsset;
    }
 

 ```
 
 
### Java 2


 ```

@Transaction()
    public MyAsset readMyAsset(String myAssetId) {
        Context ctx = getContext();
        boolean exists = myAssetExists(myAssetId);
        if (!exists) {
            throw new RuntimeException("The asset "+myAssetId+" does not exist");
        }

        MyAsset newAsset = MyAsset.fromJSONString(new String(ctx.getState(myAssetId),UTF_8));
        return newAsset;


 ```
   
  
This one starts with @Transaction(false) - the "false" means that this function is not typically intended to change the contents of the ledger. Transactions like this are typically evaluated. You'll often hear such transactions referred to as "queries". As you can see, this function only takes myAssetId, and will return the value of the whatever state that key points to.

Take a look at the other transactions in the contract at your leisure, then when you're happy, let's move on to packaging and deploying that contract so that we can start using it...
    
 <img src="img/alltuts.png">
 <p><p>Click on Tutorial 1 above
<p>
 <img src="img/tutlocal.png">
 <p>
  Follow the content in the tutorial
  
  
# III) Smart Contract overview 
 
<img src="img/scontr1.png">
 
 ---------------------------
 
<img src="img/scontr2.png">

----------------------------

<img src="img/scontr3.png">

----------------------------

 <a href="https://hyperledger-fabric.readthedocs.io/en/release-1.4/smartcontract/smartcontract.html ">Smart Contracts, see charts above</a>  

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">
 
<table>

<tr>Test of copying text rad 1</tr>
</table>

