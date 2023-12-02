# skatd-chess
Chess app built by zeeshan bari & mohammed mirajkar.

## Table of Contents
1. [Introduction, Goals, and Requirements](#introduction)
     * [Chess](#chess)
       * [Functional Requirements](#chess-func-req)
       * [Non-Functional Requirements](#chess-nonfunc-req)
       * [Possible Extended Improvements](#chess-extended-req)
     * [Messaging](#messaging)
       * [Functional Requirements](#messaging-func-req)
       * [Non-Functional Requirements](#messaging-nonfunc-req)
       * [Possible Extended Improvements](#messaging-extended-req)

# Introduction, Goals, and Requirements <a name="introduction"></a>
The idea is to emulate, only at a fundamental level, our favourite chess web app - lichess, and make improvements wherever possible.
We want to build our app for the [scale of lichess](https://www.similarweb.com/website/lichess.org/#competitors), down the line improvements, and general maintainability.
It's important to note that lichess is open source and publishes [a complete set of its entire tech stack](https://github.com/lichess-org/lila#lichessorg) but it'll be more fun to try to make it better considering we have the flexibility to perhaps make a better version. Also, I have no hope of understanding [this](https://raw.githubusercontent.com/lichess-org/lila/master/public/images/architecture.png) on first glance.
Major components are broken down below.

## Chess <a name="chess"></a>

### Requirements
#### Functional Requirements <a name="chess-func-req"></a>
1. **Guests** may sign-up/sign-in at which point they become **Users**.
2. Users/Guests should be able to play a full timed chess game with another paired, searched, friended, or anonymous player.
3. Game history should be available.
4. Elo system to rank players and communicate skill levels.
   
#### Non-Functional Requirements & Tradeoffs <a name="chess-nonfunc-req"></a>
1. Users should have a real-time search experience with minimum latency
2. PAC: Consistency of the application should be valued above availability - In the case of a partition failure, we would want to temporarily halt operations rather than allow the users to play to maintain a globally consistent game state (ie. time, moves made) ie. it would be less inconvenient for network splits to cause both sides to see a temporarily frozen game than for time mismatches between the two users in a given game.
3. ELC: Outside of network failures, we should still favour consistency over latency since despite it being a real time application, any deviance between user expereinces would not be worth the improvement in latency.

#### Possible Extended Improvements <a name="chess-extended-req"></a>
- Chess variants
- Game analytics

### Capacity Estimation and Constraints


## Messaging <a name="messaging"></a>

### Requirements
### Functional Requirements <a name="messaging-func-req"></a>
1. Player should be able to have real-time one-on-one conversations (group chats will not be supported)
2. Users should be able to view their message history with another user - guests messages will be not be stored.

### Non-Functional Requirements & Tradeoffs <a name="messaging-nonfunc-req"></a>
1. Minimum latency between users in a conversation
2. System should be highly consistent; users should see the same chat history everywhere. Availability, albeit important, is less of a concern.

### Possible Extended Improvements <a name="messaging-extended-req"></a>
- Group chats
- Push notifications
