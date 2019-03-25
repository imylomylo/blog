---
id: 441
title: 'CEO Dies &#8211; Cryptocurrency Wills &#038; Conditional Payments'
date: 2019-02-07T08:24:31+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=441
permalink: /ceo-dies-cryptocurrency-will-conditional-payments/
categories:
  - bitcoin
  - blockchain
  - cryptocurrency
  - komodo
  - smart-contracts
image: wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives.png
---
It goes without saying that the loss of a loved one is a very traumatic time.  May the family of the deceased find the time to embrace the grief and be allowed to heal without too much outside interference despite the circumstances that surround the case of the QuadrigaCX owner passing without leaving access to cold wallet keys in the form of a cryptocurrency will.

This blog post uses content from [Adrian Hope-Bailie&#8217;s post about the Interledger Protocol power of conditional payments](https://adrian.hopebailie.com/the-power-of-conditional-payments-2d1ea531250a) &#8211; the underlying technology of [Komodo&#8217;s Crypto Conditions](https://komodoplatform.com/tech-tuesday-update-7/), [UTXO smart contract and consensus customization framework](https://komodoplatform.com/crypto-conditions-utxo-based-smart-contracts/).   I&#8217;m fortunate enough to keep up to date with [recent developments of the Komodo Platform by writing a weekly Tech Tuesday](https://komodoplatform.com/tech-tuesday-update/) article.

## Basics of a conditional payment

In Adrian&#8217;s blog post linked above, Alice initiates a conditional payment to Bob.  The condition is that Bob needs to sign a receipt before the payment is released.

### Step 1

Alice sends some funds but the funds are not with Bob yet.   Bob needs to fulfill the condition.

&nbsp;<figure id="attachment_442" style="width: 1024px" class="wp-caption aligncenter">

[<img class="size-large wp-image-442" src="https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1-1024x293.png" alt="Simple conditional payment diagram" width="1024" height="293" srcset="https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1-1024x293.png 1024w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1-300x86.png 300w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1-768x220.png 768w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1.png 1432w" sizes="(max-width: 1024px) 100vw, 1024px" />](https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-bob-1.png)<figcaption class="wp-caption-text">Adrian Hope-Bailey&#8217;s conditional payment diagram.  Alice sends 100 waiting for Bob&#8217;s signature before release.</figcaption></figure> 

### Step 2

Once Bob signs a receipt and presents it, Bob receives the funds because he has met the condition for Alice&#8217;s payment to be sent.<figure id="attachment_443" style="width: 1024px" class="wp-caption aligncenter">

[<img class="size-large wp-image-443" src="https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives-1024x292.png" alt="Bob fulfills payment condition." width="1024" height="292" srcset="https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives-1024x292.png 1024w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives-300x85.png 300w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives-768x219.png 768w, https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives.png 1404w" sizes="(max-width: 1024px) 100vw, 1024px" />](https://i.mylomylo.com/wp-content/uploads/2019/02/alice-conditional-payment-met-bob-receives.png)<figcaption class="wp-caption-text">Adrian Hope-Bailey&#8217;s diagram of Bob claiming his money by presenting the fulfillment of Alice&#8217;s condition she placed for this payment.</figcaption></figure> 

&nbsp;

Very simple, it’s easy to see the value of a condition in the simple payment above between Alice and Bob. Both parties are protected by the network&#8217;s need for a condition to be fulfilled before the payment is completed.

## Conditional payments applied to a cryptocurrency will

In Komodo&#8217;s Tech Tuesday featuring the [cryptocurrency will solution being developed](https://komodoplatform.com/tt2019-4-cryptocurrency-wills-inheritance/) the above conditional payment scenario has been recreated with a multi-sig address &#8211; this is where the owner of crypto funds and the beneficiary jointly sign the release.  But with a simple condition &#8211; the owner&#8217;s address controls the funds until such time has passed where there has been no activity on the account.   Once this no-activity period has elapse, the 2nd key (the beneficiary) can spend the funds.

## How to integrate this crypto solution into a real world scenario

This solution using Crypto Conditions, and open for anyone to utilize or [build upon in their own blockchain solution](https://komodoplatform.com/blockchain-starter-kit/), including the tokenization of bitcoin or any other coin through the Gateway Crypto Condition is being heavily tested and will be available on the KMD main chain or KMDCC side chain in the near future as well as for independent 3rd party chains to adopt.

&nbsp;
