

# Flutter documentation

Flutter is an **experimental** re-implementation of FTS. Historically, FTS has relied heavily on a shared database.

## FTS2
FTS2 had a distinction between "FTS" (Service) and "FTA" (Agent). The "FTS" would interact with the users, and schedule the transfers. The FTA would run them. Typically, with FTS2 you would have a single FTS and as many "slaves" FTA as needed.
FTS2 required complex configuration to work. The system administrators had to explicitly create channels between pairs, and configure the number of transfer that they could sustain.

## FTS3
FTS3 changed heavily this design. All nodes became equals and run both scheduling and transfers. Also, and this is its killer feature, it can run with **zero** configuration, and a built-in optimizer, which works similarly to the TCP congestion algorithm, decides how many transfers a link can sustain.
However, as the number of nodes grows, the contention on the database starts being an issue, specially with lots of transfers on the queue.

## Flutter
With Flutter we want to evaluate the possibility of running a similar service based on messages, removing the need of polling a central authority. Its API will remain compatible with the one from FTS3, so we can use the same tooling (dashboard, tests...) and do a fairer comparison.
For more details, have a look at the [design](design.md) page.
