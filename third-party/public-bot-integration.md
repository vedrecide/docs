# Integrating With Your Public Bot

Developers of public bots may integrate Phisherman as a plugin to provide anti-phishing protection to their end users. This guide will provide information on the requirements for public bots.

## Authentication
Each end-user will require their own API key, which they can obtain via a request in the Phisherman [Discord server](https://discord.gg/QwrpmTgvWy).

You will need to provide an option within your users config file for them to save their API key. Your bot should then pass this key with each API request.

The flow for this should look like the following:
```:no-line-numbers
User Config -> API Key -> Your Bot -> Phisherman API
```

:::tip
An great example of how to set up Phisherman as a plugin can be found in the [Zeppelin docs](https://zeppelin.gg/docs/plugins/phisherman)
:::

## Checking Domains vs Domain Info
To ensure best performance and reliability, you should only use the [Check a domain](/api/v2/check-a-domain.md) to validate if a user-posted link is a phish or not. This endpoint is powered by Cloudflare Workers and will ensure your bot gets the quickest response on a lookup.

The [Domain Info](/api/v2/fetch-domain-info.md) endpoint should only be used to provide additional context or information to users, such as a domain info command.

![Example domain info command](/images/domain_info_embed_example.png) 

## Reporting Caught Phish
With Phisherman integration you can choose report back when it detects phishing links in servers protected by your bot. 

Reporting back caught phish is entirely optional and not required for normal usage but allows the end user to view the number of Phish they have caught in the [dashboard](https://phisherman.gg/home).

For best performance we recommend public bots use the [Bulk Reporting](/api/v2/catching-a-phish.html#bulk-reporting) endpoint.