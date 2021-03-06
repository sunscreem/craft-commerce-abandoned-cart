<p align="center"><img src="./src/icon.svg" width="100" height="100" alt="Abandoned Cart plugin for Craft Commerce 2"></p>

# Abandoned Cart plugin for Craft Commerce 2

## Requirements

This plugin requires Craft CMS 3.0.0 or later as well as Craft Commerce 2.0.0 or later.

## Abandoned Cart Overview

Abandoned Cart for Craft Commerce 2 is a plugin that provides the ability to send multiple email
reminders to customers that have abandoned their carts. This is a proven way to increase what would normally be lost revenue.

Abandoned Carts will send a maximum of two emails, these emails can be configured to be sent after a certain amount of hours.

A responsive email template is included but can be overwritten with your own if preferred.

The email the customer receives includes a link that restores their cart. 
The plugin also uses this to detect clicks. Knowing if customers are opening/clicking emails is a great way to increase conversion.

Discounts can also be included in emails. Simply create a discount code in Craft Commerce and enter that code in
Abandoned Carts settings. I recommend setting one code per email address to prevent customers taking advantage.

All abandoned cart emails are created as jobs and placed in Craft's queue, this should provide a great platform
for high performing stores.

## The settings

Any cart will be marked as abandoned 1 hour after no activity. This is important to remember when adjusting the delay settings for the reminder
emails. For example by default the 1st email will be sent 2 hours after the cart was last interacted with. Just remember to allow for that 1 hour delay upfront.

## Configuring Abandoned Cart

Once you've set your preferred email delay times all that's left to do is set up a few cron
jobs to run every few minutes (adjust this to suit your sites needs). The first cron job will look for new
abandoned carts and schedule emails.

```sh
*/5 * * * * php craft abandoned-cart/reminders/schedule-emails
```

Once abandoned cart emails have been put in the queue you'll need to tell Craft to process the queue.
You can do this by setting up a second cron job which processes any jobs in the queue.

```sh
*/1 * * * *  php craft queue/run
```

## Abandoned Cart Roadmap

Some things to look forward to:

* Dashboard widget
* Better language support
* Clean up task to remove carts after specific time
* Improved dashboard

Brought to you by [Myles Derham](https://github.com/mediabeastnz)
