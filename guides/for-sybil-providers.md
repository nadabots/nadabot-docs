---
description: For those who want to get approved to our list of checks
---

# ✅ For Sybil Providers

Want us to add your verification process inside of our human registry? \


## Benefits

* Get people sent to you through our aggregator
* Have all the applications that emit our contracts automatically integrate yourselve

{% hint style="info" %}
Have a stamp idea and want the ecosystem to build it, post on github at [https://nada.bot/request-stamp](https://nada.bot/request-stamp) OR want to build an idea the ecosysstem has had for stamp, check out the idea board at [https://nada.bot/requests](https://nada.bot/requests)
{% endhint %}

### Requirements

* Create a contract We prefer you deploy your contract under a named account, preferably as a subaccount like twitter.womrhol3.near so users can trust your entity for maintaining this contract. For example; say you create a contract that binds as twitter account to, you will create a helper function that can be called to view whether an account has successfully binded on both ends. You do not have to create a mapping contract method. For example we are not asking you return the twitter account ID, rather we just are trusting that you just verify if an account has compelted a certain check. For example on twitter.wormhol3.near you would have a method isTwitterVerified(accountId): bool. Currently it is up to the PotLock Sybil team to determine weights based on impact of check and trustworthiness of entity.
* Need a clear external link
* Make sure you are compatible with all wallets on NEAR Wallet selector&#x20;
* Create a helper view method on a contract that takes in a accountid and returns a boolean
* Add the contract name and method&#x20;
* Create a picture
* A clear description of your verification process and what you are verifying
* Add an icon for your image

First login,  click “Submit Check”, then a form will pull up. Submitting of the form requires a transaction

<figure><img src="../.gitbook/assets/Screenshot 2024-01-05 at 3.01.08 PM.png" alt=""><figcaption><p>Add A Custom Check</p></figcaption></figure>

Fill out all details about your form. Make sure you send a link. The best flow for users is to give an applciation link when after they verify their is redirect back to your check on nada.bot in order to streamline the need for users to also sign a verify transaction to add your stamp to their registry record. Also make sure to clearly describe steps and amount of gas needed.

\


<figure><img src="../.gitbook/assets/Submit Stamp for gitbook.png" alt=""><figcaption><p>Example of add a stamp / check</p></figcaption></figure>

Check out our registry contract to understand how to make your check compatible

{% content-ref url="../extra/our-contract.md" %}
[our-contract.md](../extra/our-contract.md)
{% endcontent-ref %}

### How It Works in Our System

* Afterward our bot prevention team will review the Check and then add a weight on it. (This weight can be changed)
* GIve 2-3 business days to be verified
* You will then be available for other people to verify. After they verify with you they must add a stamp (requires gas) to get their own score up, See proof you are not a bot&#x20;
* If we discover that bots are verifying with your system or any wrong doing your score can get eliminated or your check will be removed from the approve list.



### Examples of Contracts Related to Sybil Providers

* **Our Sybil Simulator Contract** [**https://github.com/PotLock/core/tree/main/contracts/sybil\_provider\_simulator**](https://github.com/PotLock/core/tree/main/contracts/sybil\_provider\_simulator)

**Other Examples**

* **Wormhol3 Twitter x NEAR Social Cross posting (WIP)** [https://github.com/wormhole3/wormhole3-account-binding](https://github.com/wormhole3/wormhole3-account-binding) (for connecting account with twitter and delegating access to contract to post on NEAR.social)
* **NDC I Am Human** [https://github.com/near-ndc/i-am-human/tree/master/contracts/human\_checker](https://github.com/near-ndc/i-am-human/tree/master/contracts/human\_checker) (uses fractal face scan for detecting)  [https://nearblocks.io/address/registry.i-am-human.near](https://nearblocks.io/address/registry.i-am-human.near) (WIP)
  *   I-Am-Human registry

      I am human is a registry contract that issues SBT based on Fractal's face verification to issue a SBT according to NEP 393. This was using in the first NDC election to verify humans for a vote. We leverage the registry is\_human method to check if someone has a face scan without the need for PotLock's contributor to keep track or having a Fractal api. &#x20;
* Holoynm (WIP) [https://github.com/holonym-foundation/v3-near-contract](https://github.com/holonym-foundation/v3-near-contract)
* **Dapplets using connected Accounts (WIP)** [https://github.com/dapplets/connected-accounts-assembly](https://github.com/dapplets/connected-accounts-assembly)
