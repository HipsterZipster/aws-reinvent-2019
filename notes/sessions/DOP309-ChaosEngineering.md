# DOP309-R Improving resiliency with chaos engineering

Failures are inevitable. Regardless of the engineering efforts put into building resilient systems and handling edge cases, sometimes a case beyond our reach turns a benign failure into a catastrophic one. Therefore, we should test and continuously improve our system’s resilience to failures to minimize impact on a user’s experience. Chaos engineering is one of the best ways to achieve that. In this session, you learn how Amazon Prime Video has implemented chaos engineering into its regular testing methods, helping it achieve increased resiliency.

**Speakers**

- Adrian Hornsby - Principal Evangelist, Amazon Web Services
- Olga Hall - Senior Manager, Tech Program Management

**Session Info**

- Session Level:300 - Advanced
- Monday, Dec 2, 5:30 PM - 6:30 PM
- Venetian, Level 2, Venetian E

## GameDay at Amazon

- Created gameday in 2004 to purposefully create regular major failures

## Rise of the monkeys

- "simian army to keep our cloud safe, secure, and highly available" - 2011 netflix blog
- netflix formalized chaos engineering in mid-2015

#### Examples:

- set of scheduled agents
- shut down services readonly
- slow down perf
- check conformity
- break an entire region
- integrate with Spinaker

**principlesofchaos.org**

- Chaos engineering is not a about breaking things randomly without a purpose
- Chaos engineering is about breaking things in a controlled environment and through well-planned experiments in order to build confidence in your application to withstand turbulent conditions.

### Phases of chaos engineering

- steady state
- hypothesis
- run experiment
- verify
- improve

#### What is steady state

- normal behavior of your system
- not the internal attributes of the system (CPU, memory, etc)
- operational metrics tied with customer experience yields best results
- the steady state varies when an unmitigated failure triggers an unexpected problem and it should cause the chaos experiment to be aborted

### What if...?

- What if this load balancer breaks?
- What if redis becomes slow?
- What if a host goes away
- What if latency increases by 300ms
- What if the database stops

#### Failure Injection

**Start small and build confidence**

- Application level (exceptions, errors, etc)
- host level (services, processes, etc)
- Resource attacks (CPU, memory, IO, etc)
- Network attacks
- AZ attack
- Region attack
- People attack

### Quantifying the result of the experiment

- Time to detect?
- Time for notification and escalation
- Time to public notification
- Time for graceful degradation

### Postmortems COE (Correction of Errors)

- What happened?
- What was the impact on customers and your business
- What were the causes? The 5 whys - not linear
- What data do you have to support this?

### Big challenges to Chaos Engineering

- chaos engineering wont make your system more robust, people will
- chose engineering wont replace **all** the rest (test, quality, etc)
- can be very political
- might force deep conversations
- deeply investigated in a specifically technological roadmap that chaos engineering tests show is not as resilient

## From Chaos to Resilience - Prime Video

- readiness to handle failure (or the unknown) is feature zero
- how would you predict this pattern?
  - customers subscribing a minute before the show starts
  - customers rewatching
- little's law: number of customers in system = arrival rate x mean time in system
