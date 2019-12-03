# DOP342-R Amazon's approach to building resilient services

One of the biggest challenges of building services and systems is predicting the future. Changing load, business requirements, and customer behavior can all change in unexpected ways. In this talk, we look at how AWS builds, monitors, and operates services that handle the unexpected. Learn how to make your own services handle a changing world, from basic design principles to patterns you can apply today.

**Speakers**

- Marc Brooker - Senior Principal Engineer, Amazon Web Services

**Session Info**

- Session Level:300 - Advanced
- Monday, Dec 2, 1:45 PM - 2:45 PM
- Venetian, Level 2, Venetian Theatre

### The DevOps Loop

- build, fail, analyze causes of failure, change practices

## What risks?

- outright project failure

### how we do this at AWS

- Teams run what they build
- Principal engineers are builders (avoid non-practitioners architects)
- Everybody has operational responsibility
- Correction of error (COE) reviews connect broad sets of builders and operators

### Organizationally

- Small teams
- Strong ownership

### Operationally

- deploy often
- dive deep on issues
- create mechanisms to drive learning back to implementation
- have mechanisms to close the loop

# Operational Safety - Setting operators up for success

- "The scram just before the sharp rise in power that destroyed the reactor may well have been the decisive contributory factor" - IAEA INSAG-7

- "How and why should the operators have compensated for the design errors they did not know about?" - anatoly dyatlov "Why insag has still got it wrong april 2006

## Kind and wicked learning environment

- kind: the things we learn match the environment well. more experience means better predictions and better judgement (The two settings of kind and wicket learning environments" current direction in psychological science 2015

- wicked: the things we learn don't match the environment. our experience leads us to do the wrong thing.

### build your systems to be kind - how we do it as AWS

- Correction of error process doesn't settle for operator error
- reviewing tooling is critical work for the most senior engineers.

### operators are easy to blame

- they made the mistake - (managers and architects have no responsibility)
- we fired them (the issue is fixed with little effort)
- they no longer work here (no need to be worried)

**Leadership must reject this thinking**

## 3 books for future reading

- see pics

## Dog Sliding off Roof example

- dog sliding off the room equation
- the coefficient of static friction (it's the amount of resistance you get when the dog stopped sliding)
- the dog starts sliding and then can't stop sliding
- kinetic friction is always less then static friction
- distributed systems have the same problem of instability
- system becomes overloaded -> load increases latency -> timeouts cause failures -> retries add load

### How we do this at AWS

- Limit queue sizes
- Exponentially back on retry
- Limit retries if possible
- End-to-end back pressure

## Jitter

- Add some jitter and randomness (choose a random number) to your retries logic to increase capacity
- screenshot before and after
- What is the best way to add Jitter to retries?
- each time you back off `randint(0, base * 2 ** attempt)`

### How do they do this at AWS

- always jitter when using backoff
- always jitter periodic work (timers, cron, etc)
- consider adding jitter to all work

# Summary

- Ownership: closing the loop between dev and ops
- operational safety - setting operators up fort success
- service stability - what it means to be stable at scale
- jitter - how randomness can add resilience

### Key Takeaway: Success requires culture and technology
