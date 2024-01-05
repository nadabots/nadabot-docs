---
description: For those who want to get approved to our list of checks
---

# ✅ For Sybil Providers

Want us to add your verification process inside of our human registry? \


## Benefits

* Get people sent to you through our aggregator
* Have all the applications that emit our contracts automatically integrate yourselve

\


### Requirements

* Create a contract
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

* **Wormhol3 Twitter x NEAR Social Cross posting** [https://github.com/wormhole3/wormhole3-account-binding](https://github.com/wormhole3/wormhole3-account-binding) (for connecting account with twitter and delegating access to contract to post on NEAR.social)
* **NDC I Am Human** [https://github.com/near-ndc/i-am-human/tree/master/contracts/human\_checker](https://github.com/near-ndc/i-am-human/tree/master/contracts/human\_checker) (uses fractal face scan for detecting)  [https://nearblocks.io/address/registry.i-am-human.near](https://nearblocks.io/address/registry.i-am-human.near)
* **Dapplets using connected Accounts** [https://github.com/dapplets/connected-accounts-assembly](https://github.com/dapplets/connected-accounts-assembly)
