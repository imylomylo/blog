---
id: 258
title: Serverless AWS SES Email Address Policy
date: 2018-04-10T05:36:50+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=258
permalink: /serverless-aws-ses-email-address-policy/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2018/04/permissions.png
categories:
  - aws
  - serverless
---
The advantages of serverless are sometimes taken away by all the configuration to make the thing work &#8211; securely.  But 3 hours today saves 100 hours throughout the year.

This is the manual method of setting up a policy that is not FullAdministrator mode.  It can be further locked down if you were doing government/policy strict work, and you&#8217;d want to do it programmatically so it&#8217;s automated and auditable.

## User with Lambda, SES, API Gateway and CloudFormation Full Access

[<img class="aligncenter wp-image-259 size-large" src="https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email-997x1024.png" alt="AWS IAM Policy for Serverless" width="640" height="657" srcset="https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email-997x1024.png 997w, https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email-292x300.png 292w, https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email-768x788.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email.png 1091w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2018/04/IAM-policy-serverless-lambda-email.png)

## Serverless Errors From Email Address Send To Permissions

<img class="aligncenter wp-image-260 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/04/serverless-resource-permission-email-sandbox.png" alt="Serverless resource permissions" width="1021" height="290" srcset="https://i.mylomylo.com/wp-content/uploads/2018/04/serverless-resource-permission-email-sandbox.png 1021w, https://i.mylomylo.com/wp-content/uploads/2018/04/serverless-resource-permission-email-sandbox-300x85.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/04/serverless-resource-permission-email-sandbox-768x218.png 768w" sizes="(max-width: 1021px) 100vw, 1021px" /> 

## Add Policy For Receiver Address

[<img class="aligncenter wp-image-261 size-large" src="https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy-1024x616.png" alt="SES Email Address Policy" width="640" height="385" srcset="https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy-1024x616.png 1024w, https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy-300x181.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy-768x462.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy.png 1113w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2018/04/ses-email-address-add-policy.png)

&nbsp;

Then you can deploy your app with full deploy and sending email capabilities.