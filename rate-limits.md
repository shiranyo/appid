---

copyright:
  years: 2017, 2019
lastupdated: "2019-12-18"

keywords: rate limits, traffic control, limit request, lite instances, per minute, per instance, per user, limits

subcollection: appid

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}


# {{site.data.keyword.appid_short_notm}} limits
{: #limits}

Rate limiting is used to control the amount of traffic that is coming and going through your instance of {{site.data.keyword.appid_full}}. By limiting requests or resources, you can protect your applications.
{: shortdesc}

## {{site.data.keyword.appid_short_notm}} lite plan
{: #lite-limits}

Review the following table to see the limits that are in place for lite instances of {{site.data.keyword.appid_short_notm}}.

<table>
    <caption>Table 1. Limits for lite instances</caption>
    <tr>
        <th>Resource</th>
        <th>Maximum</th>
    </tr>
    <tr>
        <td>Users</td>
        <td>1000</td>
    </tr>
    <tr>
        <td>Authentications</td>
        <td>1000 per month</td>
    </tr>
</table>

## General
{: #general-limits}

The following table lists the maximum per user limits for {{site.data.keyword.appid_short_notm}} resources and the blocking period when the limits are exceeded. These limits apply to any user who can create {{site.data.keyword.appid_short_notm}} resources.
{: shortdesc}

<table>
    <caption>Table 2. General rate limits</caption>
    <tr>
        <th>Action</th>
        <th>Limit</th>
        <th>When Exceeded</th>
    </tr>
    <tr>
        <td>Sign in attempts by one user</td>
        <td>11 per minute</td>
        <td>User unable to sign in for 1 minute.</td>
    </tr>
    <tr>
        <td>Update user profile attributes</td>
        <td>5 per minute</td>
        <td>User unable to update profile for 1 minute.</td>
    </tr>
        <td>Delete user profile attributes</td>
        <td>5 per minute</td>
        <td>User unable to update profile for 1 minute.</td>
    </tr>
    <tr>
      <td>Applications per {{site.data.keyword.appid_short_notm}} instance</td>
      <td>50</td>
    </tr>
</table>



## Cloud Directory
{: #limits-cd}

Review the following table to see limits that are associated with Cloud Directory.
{: shortdesc}

<table>
    <caption>Table 3. Cloud Directory limits</caption>
    <tr>
        <th>API</th>
        <th>Configurable</th>
        <th>Limit</th>
        <th>When Exceeded</th>
    </tr>
    <tr>
        <td>Sign in attempts per account</td>
        <td>Yes</td>
        <td>Unlimited</td>
        <td>All sign-in attempts for the instance are blocked for one minute.</td>
    </tr>
    <tr>
        <td>Sign up attempts per account</td>
        <td>Yes</td>
        <td>Unlimited</td>
        <td>All sign-up attempts for the instance are blocked for one minute.</td>
    </tr>
    <tr>
        <td>Email sending request</td>
        <td>No</td>
        <td>10 emails in 5 minutes per user</td>
        <td>Email requests for the user are blocked for 30 minutes.</td>
    </tr>
    <tr>
        <td>SMS sending request</td>
        <td>No</td>
        <td>10 SMS in 5 minutes per user</td>
        <td>SMS requests for the user are blocked for 30 minutes.</td>
    </tr>
    <tr>
        <td>MFA code characters</td>
        <td>No</td>
        <td>6 numeric characters</td>
        <td>The code automatically has 6 characters that must be input by the user.</td>
    </tr>
    <tr>
        <td>MFA code expiration</td>
        <td>No</td>
        <td>15 Minutes</td>
        <td>If a user does not validate their code within 15 minutes, they can request that another code is sent as long as the authentication session is not expired. Within the authentication session, the code can be sent multiple times. Once the authentication session expires, the user must repeat the login process from the beginning.</td>
    </tr>
</table>

For more information, see the [rate limit management API](https://us-south.appid.cloud.ibm.com/swagger-ui/#/Management%20API%20-%20Config/mgmt.updateRateLimitConfig){: external}.


## Ingress annotation
{: #annotation-limits}

Be sure to review the following limitations before you configure your annotation.


* Refresh tokens are not currently supported.
* {{site.data.keyword.containerlong}} supports one Ingress per namespace. If you already have one, you can update the existing Ingress configuration or use a different namespace.


## Extensions
{: #limits-extensions}

### Pre-MFA
{: #limits-premfa}

* The response from your extension point must not exceed 10KB. If it does, the request is aborted and the user is required to complete MFA.
* If it takes {{site.data.keyword.appid_short_notm}} longer than 5 seconds to establish a connection to your extension point, or if the request takes longer than 7 seconds to complete, the request is aborted and the user is required to complete MFA.
