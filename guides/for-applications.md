---
description: For application looks for a sybil resistance Solution
---

# 📱 For Applications

If you want to integrate us this usually means you are building an application on NEAR and either

* **Front End Gating:** check a user logged is a human to display different views
* **NEAR Contracts**: using for a cross contract call to our registry to enforce on the contract level

## Front End Gating

### BOS/NEARJS

[NEARJS](https://docs.near.org/bos)/BOS is a framework for front end development that stores front end JSX code on chain that can be accessed across different gateways / web apps that support the BOS VM. NEAR API JS is built in. Here is an easy way to detect human checks

#### Check Contract for Human

{% hint style="info" %}
Humans are calculated by adding assigned weights of stamps a user has, against a set of rules of how stamps interacts, against a human threshold. If the account that is being checked passes the human threshold score after being called than an account is considered a human
{% endhint %}

[https://near.social/plugrel.near/widget/nadabot\_human](https://near.social/plugrel.near/widget/nadabot\_human) (Example of BOS helper component)

```jsx
// check is_human method that enables
const accountId = props.accountId ?? "odins_eyehole.near";

Near.asyncView("v1.nadabot.near", "is_human", { account_id: accountId }).then(
  (result) => {
    State.update({ human: result });
  }
);

return <>{state.human && <span>✅</span>}</>;

```

#### Check Contract for Human Score

```jsx
 // check human score of account from https://near.social/mob.near/widget/WidgetSource?src=plugrel.near/widget/nadabot.checkHumanScore
 
const accountId = props.accountId ?? "odins_eyehole.near";
const staging = props.staging ?? false;
const contract = staging ? "v1.staging.nada.bot" : "v1.nadabot.near";
Near.asyncView(contract, "get_human_score", {
  account_id: accountId,
}).then((result) => {
  State.update({ score_result: result });
});
// console.log(state.score.score);
return <>{state.score_result && <span>{state.score_result.score}</span>}</>;
```

## VanillaJS

Check out the NEAR Docs to get a better sense of how to integrate in the front end. If you are using a javascript front end library you will most likely be integrating with our contract via NEAR API JS



```bash
npm install near-api-js near-wallet-selector
```

{% embed url="https://docs.near.org/tools/near-api-js/quick-reference" %}

In your javascript app

#### Check Human and Human Score

{% embed url="https://github.com/PotLock/helpful-js/blob/main/isHuman.js" %}

```javascript
const { connect, keyStores, utils } = require('near-api-js');

async function checkHuman(accountId) {
    // Configure the connection to the NEAR blockchain
    const near = await connect({
        networkId: "mainnet",
        keyStore: new keyStores.InMemoryKeyStore(),
        nodeUrl: "https://rpc.mainnet.near.org",
        walletUrl: "https://app.mynearwallet.com/"
    });

    // Use a generic account for contract calls
    const staging =  false;
    const contract = staging ? "v1.staging.nada.bot" : "v1.nadabot.near";
    const account = await near.account(accountId);

    // Fetch all donations
    const isHuman = await account.viewFunction({
        contractId: contract,
        methodName: "is_human",
        args: {account_id: accountId}
    });

    console.log(isHuman);

    // Return the top donors and their streaks
    return isHuman;
}

async function humanScore(accountId) {
    // Configure the connection to the NEAR blockchain
    const near = await connect({
        networkId: "mainnet",
        keyStore: new keyStores.InMemoryKeyStore(),
        nodeUrl: "https://rpc.mainnet.near.org",
        walletUrl: "https://app.mynearwallet.com/"
    });

    // Use a generic account for contract calls
    const staging =  false;
    const contract = staging ? "v1.staging.nada.bot" : "v1.nadabot.near";
    const account = await near.account(accountId);

    // Fetch all donations
    const score = await account.viewFunction({
        contractId: contract,
        methodName: "get_human_score",
        args: {account_id: accountId}
    });

    // returns score
    return score.score;
}

// change with the account you wan to check
const testAccount = "odins_eyehole.near"; 
// call just human
checkHuman(testAccount).then(isHuman => {
    // Additional handling if needed
}).catch(error => {
    console.error("Error checking for human:", error);
});
// to get score, also returns is human but just pull score
humanScore(testAccount).then(score => {
    // Additional handling if needed
}).catch(error => {
    console.error("Error checking for human score:", error);
});


```

Some notes about the code snippet

* **Interact with NEAR Blockchain**: Utilizes `near-api-js` to connect to the NEAR mainnet and interact with a specified smart contract, handling blockchain operations like querying account details and executing contract methods.
* **Verify Human Status**: The `checkHuman` function checks if a given NEAR account is recognized as human by calling the `is_human` method on the smart contract, useful for differentiating between automated bots and human users.
* **Retrieve Human Score**: The `humanScore` function queries the smart contract for a "human score" associated with the account, providing a quantitative measure of the account's human-like behavior or verification status via the `get_human_score` method.
* **Configurable for Environments**: Supports switching between staging and production environments by altering the contract address, allowing for flexible testing and deployment scenarios.
* **Asynchronous and Error Handling**: Implements asynchronous JavaScript patterns for non-blocking calls to the NEAR blockchain and includes error handling for robust operation and debugging.

Make sure to handle the UI elements (like the popup modal) according to your application's frontend framework or library. The above code assumes a basic JavaScript setup and will need to be adapted to fit your specific implementation details.

## NEAR Contract

NEAR Protocl is a layer 1 blockchain with Rust contracts that compile to Wasm.&#x20;

**Create Your First Rust Contract**: After installing Rust, you can create your first Rust contract. Here are the steps:

* Download and install [Rust](https://doc.rust-lang.org/book/ch01-01-installation.html).
* Create a new Rust project using the [quickstart guide](https://app.hzn.xyz/2.develop/quickstart.md).
* Read the NEAR docs on [how to write smart contracts](https://app.hzn.xyz/2.develop/contracts/anatomy.md).

**Resources**: For more information and examples, you can refer to the following resources:

* Documentation: https://docs.near.org/develop/contracts/anatomy&#x20;
* Examples: https://docs.near.org/tutorials/welcome
* Github: https://github.com/near/near-sdk-rs

### Cross Contract Calls

{% embed url="https://github.com/near/docs/blob/master/docs/sdk/rust/cross-contract/callbacks.md" %}

Here is an example with how nada.bot does it with I-Am Human contract [https://github.com/PotLock/core/blob/71f35051f81c333c85fafc42d073173191ad14ca/contracts/sybil/src/human.rs#L43](https://github.com/PotLock/core/blob/71f35051f81c333c85fafc42d073173191ad14ca/contracts/sybil/src/human.rs#L43)



To make a cross-contract call in Rust for a NEAR smart contract, you would typically use the `promise_then` method to schedule the execution of a callback after the initial cross-contract call completes. Here's a basic example of how you might structure this in your Rust smart contract:

```
```



```rust
use near_sdk::borsh::{self, BorshDeserialize, BorshSerialize};
use near_sdk::{env, near_bindgen, Promise, AccountId};
use near_sdk::json_types::U128;

#[near_bindgen]
#[derive(Default, BorshDeserialize, BorshSerialize)]
pub struct MyContract {
    // Your contract's state and fields go here
}

#[near_bindgen]
impl MyContract {
    pub fn call_is_human(&self, account_id: AccountId) {
        let sybil_contract: AccountId = "v1.nadabot.near".parse().unwrap();

        // Call `isHuman` method on the sybil_contract
        Promise::new(sybil_contract)
            .function_call(
                "isHuman".to_string(),
                // Here you would serialize the parameters for the `isHuman` method
                // For this example, assume that it takes an account_id in JSON format
                serde_json::to_vec(&account_id).unwrap(),
                0, // attached deposit
                env::prepaid_gas() / 2 // use half of the remaining gas
            )
            .then(
                // Schedule the execution of the callback method
                env::current_account_id(),
                "on_is_human_callback".to_string(),
                // You can pass any additional data needed for the callback here
                // In this case, we're not passing any extra data
                vec![],
                0, // attached deposit for the callback
                env::prepaid_gas() / 2 // use the remaining half of the gas
            );
    }

    // Callback function
    pub fn on_is_human_callback(&mut self) {
        // Here you would handle the result from the `isHuman` call
        // Assuming the result is a boolean
        let is_human: bool = match env::promise_result(0) {
            near_sdk::PromiseResult::Successful(result) => {
                // Deserialize the result to a bool
                serde_json::from_slice::<bool>(&result).unwrap_or(false)
            }
            _ => false,
        };

        // Store or use `is_human` as needed
        let is_valid = is_human;
        // Further logic depending on `is_valid`
    }
}

// Boilerplate code for tests and initialization goes here

```

## Ideas to Integrate

* Airdropping and amplified rewards for loyalty programs
* 1 person 1 vote for governance on governance contract
* Quadratic funding
* Human based fees
