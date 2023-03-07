# Orgspace pairing challenge

## Why?

There's a rich discourse in software development about how to assess candidates. At Orgspace, we believe the following:

* Interviewing is a stressful and often biased and inequitable process, but it's nonetheless important that we assess candidates as people and as technologists to find a mutual fit.
* So-called "algorithmic" challenges are a poor predictor of the skills, capabilities and attitudes that lead to better software. 
* Collaboration is often a powerful model for working, and a good way to give candidates the ability to assess and challenge their interviewers.
* We want everyone to walk out of the process feeling successful and respected.

Therefore:

* We rely on an intentionally lightweight challenge, meant as the starting point for a conversation on approach and values.
* We invite candidates to pair-program with us on the solution to that challenge, though they may if they prefer complete it on their own, followed by a code review interview.
* We try to be explicit about what we expect and what we're looking for—no guesswork involved.
* We avoid surprise puzzle questions that the only reviewer (or an experienced interviewee) has already heard the answer to.

### What we're looking for in a solution

* When pairing:
  * Is the candidate respectful, energetic, positive, collaborative, responsive to feedback?
  * Does the candidate demonstrate fluency and speed with their tools and programming idioms of choice?
  * Does the candidate ask good questions about the business domain, gaps and edge cases of the challenge?

* As code:
  * Is the solution plausibly correct, well-written, balanced between simple and extensible?
  * How does the solution telegraph a commitment to quality, both in code and in output?
  * Does the code demonstrate fluency with Typescript and functional-style programming?

### Meta

This skeleton repo includes a single executable file, `src/summary.ts`. I've used [bun](https://bun.sh/) below, but you may execute it using `ts-node` or whatever you like. Suggestions on how to standardize this are welcome.

### Testimonial

> [This kind of technical assessment] remains the gold standard for interviewing, in my experience, as both interviewer and interviewee. Well done, Brian and team, for promoting this practice.

[David Rupp, Senior Software Development Engineer, AWS](https://www.linkedin.com/posts/davidrupp_github-orgspaceiopairing-exercise-orgspace-activity-7030520175439343616-cdIQ)

<br>
<br>
<hr>

## Challenge

*Given an ordered sequence of events of this type, read from `stdin`:*

| Event type                | Entity   | Payload type                        |
| ------------------------- | -------- | ----------------------------------- |
| `PersonCreated`           | `Person` | `{id: string, name: string}`        |
| `TeamCreated`             | `Team`   | `{id: string, name: string}`        |
| `PersonAssignedToTeam`    | `Person` | `{id: string, teamId: string}`      |
| `PersonAssignedToManager` | `Person` | `{id: string, managerId: string}`   |

*Output the following summary:*

* Total team count
* Total person count
* Person with the most number of direct reports
* Team with the most assigned people

*Example:*

```sh
$ cat << EVENTS | bun src/summary.ts
 {"type": "PersonCreated", "payload": {"id": "guybrush", "name": "Guybrush Threepwood"}}
 {"type": "PersonCreated", "payload": {"id": "elaine", "name": "Elaine Marley"}}
 {"type": "PersonAssignedToManager", "payload": {"id": "guybrush", "managerId": "elaine"}}
EVENTS

Total team count: 0
Total person count: 2
Manager with most direct reports: Elaine (2)
Team with most people assigned: N/A
```
