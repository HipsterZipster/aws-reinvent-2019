---

DOP342-R - [REPEAT] Amazon's approach to building resilient services

One of the biggest challenges of building services and systems is predicting the future. Changing load, business requirements, and customer behavior can all change in unexpected ways. In this talk, we look at how AWS builds, monitors, and operates services that handle the unexpected. Learn how to make your own services handle a changing world, from basic design principles to patterns you can apply today.


Marc Brooker - Senior Principal Engineer, Amazon Web Services
Additional Information
Session Type:Session
Topic:DevOps
Session Level:300 - Advanced
Please note that session information is subject to change.
Session Schedule
Monday, Dec 2, 1:45 PM - 2:45 PM
– Venetian, Level 2, Venetian Theatre

### The DevOps Loop
- build, fail, analyze causes of failure, change practices

## What risks? 
- outright project failure

### how we do this at AWS
- Teams run what they build
- Principal engineers are builders (avoid non-practioners architects)
- Everybody has operational responsibility
- Correction of error (COE) reviews connect broad sets of builders and operators

### Organizationally
- small teams
- strong ownership

### Operationally
- deploy often
- dive deep on issues
- create mechanisms to drive learning back to implementation
- have mechanisms to close the loop


# Operational Safety - Setting operators up for successs

- "The scram just before th esharp rise in power that destroyed the reactor may well have been the decisive contributory factor" - IAEA INSAG-7

- "How and why should the operators have compensated for the design errrors they did not know about?" - anatoly dyatlov "Why insag has still got it wrong april 2006


## Kind and wicked learning environment
- kind: the things we lern match the envrionment well. more experience means better predictions and better judgement (The two settings of kind and wicket learning environments" current direction in psychological science 2015

- wicked: the things we learn dont match the environemnt. our experience leads us to do the wrong thing. 

### build your systems to be kind - how we do it as AWS
- Correction of error process doesn't settle for operator error
- reviewing tooling is critical work for the most senior engineers.

### operators are easy to blame
- they made th emistake - (managaers and artchitects have no responsibility)
- we fired them (the issue is fixed with little effort)
- they no longer work heree (no need to be worried)

**Leadership must reject this thinking**