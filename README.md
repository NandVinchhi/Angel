![](angel.png)

[![Robin](https://img.shields.io/badge/bot-angel-00B4FF.svg?style=for-the-badge)](https://robin.silentbyte.com)&nbsp;
[![Status](https://img.shields.io/badge/status-live-00B20E.svg?style=for-the-badge)](https://robin.silentbyte.com)&nbsp;

<!-- [![Donate](https://img.shields.io/badge/buy_me_coffee-donate-DFB217.svg?style=for-the-badge)](https://robin.silentbyte.com) -->

# Angel Assistant

Angel is an intelligent medication tracking assistant powered by [Wit.ai](https://wit.ai/). This project was submitted to the [Facebook Artificial Intelligence Hackathon](https://fbai2.devpost.com/) and [Facebook Messaging Hackathon](https://fbai2.devpost.com/).

Want to use Angel Assistant? Start a conversation by messaging at https://facebook.com/angelassistantai.

Our project website is https://angelassistant.tech/.

## Inspiration

Budgeting and personal finance is a challenge for many people, and a large percentage of the population lives paycheck-to-paycheck, having little to no savings. Extreme circumstances like the current Covid-19 pandemic affect the most vulnerable people the most.

We have decided to leverage the power of Wit.ai to build an easy-to-use chat bot that assists people with budgeting and tracking expenses in an effort to empower people to stay on top of their finances and to put some fun into personal finance. Wit.ai supports a direct and natural way to interact with technology through language, making book-keeping easy and accessible.

## What it does

Robin allows users to quickly set up a budget and keep track of expenses. Users can add expenses whenever they occur just by pulling out their phones and leaving a text or quick voice message. Robin is then able to do calculations on these expenses and tell the users how much of their weekly budget is left, when expenses have been incurred, what expenses have been incurred over what period of time, and so on.

## How we built it

Robin lives inside of a TypeScript Cloud Function and is hosted on Firebase. Incoming messages from Messenger and Telegram get forwarded to Robin for processing. Messages are analyzed based on the current state of the conversation (backed by a database and a state machine) and are then forwarded to Wit.ai, which returns a list of intents, entities, and traits (we have also implemented support for voice message and audio conversion). We then process those intents, entities, and traits, and match them against the current state of the conversation. Robin then produces a list of reply messages to be send back to the user and a list of actions to be carried out, along with the new state of the conversation that is then persisted in the database and loaded again once the next message for the particular user arrives.

## Challenges we ran into

As mentioned above, the implementation of a chat bot's logic can become very complex very quickly. The major challenge we faced was dealing with that complexity in a way that allows more functionality to be added without increasing complexity exponentially. Another challenge we faced goes hand-in-hand: debugging complex, interwoven state can be difficult and time-consuming. Extensive logging and tracing really helped a lot here and is something to remember for the next project. Finally, we had to come up with a custom solution to support voice messages because Wit.ai does not natively support the voice message formats of Telegram/Messenger.

## Accomplishments that we're proud of

We were proud to have created a well-designed and well-executed Minimum Viable Prototype of an intelligent chat bot that successfully tracks medications, and implements various tracking features. The system integrates well with Messenger, and we strive to integrate it with other chat platforms as well in the future. Lastly, we are proud to have configured natural language interactions by enabling users to send custom voice messages.

## What we learned

Sometimes things that seem simple on the surface turn out to be much more difficult when observed in detail. The first few Wit.ai intents were quickly implemented (e.g. tell_joke and greeting), but the more complicated ones such as add_expense quickly lead to a state explosion that required us to change our approach from a direct implementation of the logic to an indirect solution through a state machine. We also learned that it is a good idea to keep things more generic from the start in order to be able to support multiple back-ends (Messenger/Telegram) without excessive refactoring sessions.

## What's next for Angel Assistant

Currently, Angel Assistant is designed and published as a Minimum Viable Product. We would like to refine the functionality, taking into consideration feedback from users and experts in the healthcare field. A feature we would especially like to implement is support for finding and showing further information on various medications, as well as integrating with pharmacy systems for online purchases of medications.

---

## Build Instructions

1. Set up your [Wit.ai](https://wit.ai/) and create [Messenger](https://developers.facebook.com/docs/messenger-platform/) bots to get your access keys.

2. Install Python and Flask via pip, and and update the access keys for the bot.

3. Start the ngrok server by running server.py.

4. Test using messenger

5. Alternatively, message https://facebook.com/angelassistantai to start chatting now!
