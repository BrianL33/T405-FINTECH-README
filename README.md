# Investing in Wine through NFTs 

Digitalization of the wine industry and lowering the barrier of entry for wine investment through NFT


## WHY WE NEED TO USE NFT FOR WINE INVESTMENT 

 - [Illegal according to the Food and Environmental Hygiene Department](https://www.fehd.gov.hk/english/licensing/ll-cll-appguide.pdf)
 - Through the usage of NFT and our proposal, it becomes a trade of assets and not an illegal investment activity
 - Wines' values increase over time and customers can profit from investing into high-end value wine 
 - Digitalization of the wine industry can attract more younger generations 
 - High-end value wines become easily accessible all around the world through our proposal
 - Our proposal is more than selling just a bottle of wine/liquor
 
 and we will aim to achieve our proposal through a platform called Immutable X. 
 # Technology Used: Immutable X
## HOW WE USE IMMUTABLE X
### Setting  Up for business 
 Throughout this project, we will be mainly focused on using Typescript 
 - [Basic guide to setting up for Immutable X](https://docs.x.immutable.com/docs/how-to-install-initialize#core-sdk) 
### Connecting customers' wallets to Immutable X  
We will aim to register customers by connecting to their wallets (preferably Metamask)
- Transaction histories are constantly updated into the blockchain
- Any operations require customers' signature, which provides additional security 
[How to connect customers' wallets](https://docs.x.immutable.com/docs/how-to-generate-signers/#connect-to-users-wallets)

Install Wallet SDK npm package: 

```typescript
npm install @imtbl/wallet-sdk-web --save
```
### Customer Registration 
[How to register customers on Immutable X](https://docs.x.immutable.com/docs/how-to-register-users/#core-sdk)

Example of how to register the Customers: 

```typescript
const walletConnection = { ethSigner, starkSigner }

client.registerOffchain(walletConnection)
```

## Creating Products for Sale 
### Setting Parameters 
- No more than 3 receipients
- Can't set the same recipient multiple times
- Combined fee can't be more than 100% 
- Individual percentage fee can't be less than or equal to 0
[Typescript Core SDK Parameters](https://docs.x.immutable.com/docs/how-to-create-orders/)
### Creating the products
[How to create products on Immutable X](https://docs.x.immutable.com/docs/how-to-create-orders/) 

Example of creating a product:

```typescript
const createOrder = async (
  wallet: WalletConnection, // WalletConnection containing the L1 and L2 signers
  orderData: UnsignedOrderRequest // Order Data from the previous step
) => {
  const response = await client.createOrder(wallet, orderData);
  return response;
};
createOrder(wallet, orderData)
  .then((result) => {
    console.log(result);
  })
  .catch((e) => {
    console.log(e);
  });
  ```
  
  Example Response: 
  
  ```typescript
{
  order_id: 7215, // ID of the created order
  status: '', // Status of the created order
  time: 0 // Timestamp of the created order
}
  ```

## Enabling Trade 
[How to enable trade on Immutable X](https://docs.x.immutable.com/docs/how-to-create-trades/#core-sdk) 

Example of creating trade with Wallet ID 7232: 

```typescript
const createTrade = async (wallet: WalletConnection, orderId: number) => {
  const ethAddress = await wallet.ethSigner.getAddress();
  const tradeData = {
    order_id: orderId,
    user: ethAddress
  } as GetSignableTradeRequest;
  const response = await client.createTrade(wallet, tradeData);
  return response;
}
createTrade(wallet, 7232)
  .then((result) => {
    console.log(result)
  })
  .catch((e) => {
    console.log(e)
  })
  ```
  
Response Example: 
  
```typescript
{ 
  trade_id: 226892, // ID of trade within ImmutableX
  status: '' // Current status of trade
}
  ```
  
## NFT Artwork 
We wish to collaborate with NFT artists around the world to create unique NFT artworks, which will represent our wine bottles' history
### Minting NFTs with royalties 
[How to mint NFTs with royalties](https://docs.x.immutable.com/docs/minting-with-royalties/)

- Minting NFTs with royalties can reward the NFT artists 
- Keep track of the transaction histories of the NFTs 
## License of Immutable X

[Immutable X](https://support.immutable.com/en/articles/6393972-immutable-x-protocol-licence-agreement)
