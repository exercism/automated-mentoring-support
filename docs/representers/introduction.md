# Introduction to Representers

One of the problems faced by the Exercism community is how to provide meaningful feedback to many people providing many solutions to many different exercises. To help reduce the scope of this potentially enormous task, solutions are normalized into "representations". For example, out of the most recent 500 submissions to the TwoFer exercise on the Ruby track, about 380 of them would be considered unique (if you normalize for trivial things like code formatting and comments). If you normalise them even further (by normalizing things like function or variable names), that number gets even smaller, so there might be only 250 unique approaches. If the Exercism community can provide some feedback on those 250 approaches, then hope is that we will have valid feedback prepared for ~99% of all future submissions for TwoFer. With the Concept Exercises the solution space will be even smaller because Concepts Exercises will be deliberately designed to solved in a specific way.

A _representer_ is a bit of code that has the single responsibility of taking a solution and returning a normalized representation of it. 

A _representation_ is an extraction of a solution to its essence with normalized names, comments, spacing, etc. but still uniquely identifying the approach taken. Two different ways of solving the same exercise must not have the same representation.

The simplest representer is one that merely returns the solution's source code. However, as our goal is to have the same representation for solutions only differing in non-essential details, the representer should apply one or more [normalizations](./normalization.md).

Once we have a normalized representation for a solution, a team of vetted mentors will look at the solution and comment on it (if needed). These comments will then automatically be submitted to each new solution with the same representation. A notification will be sent for old solutions with a matching representation.
