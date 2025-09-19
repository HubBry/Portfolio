# SQL and ETL Examples

I've been surprised at the robustness of the <a href="https://leetcode.com/">LeetCode platform</a>, and I've got a few examples of the <a href="https://leetcode.com/studyplan/top-sql-50/">SQL 50!</a>

## SQL 50

The SQL 50 is a great collection of challenges that require skill in applying basic joins, select statements, aggregate functions, subqueries, strings... with a whole host of solutions and guidance available from the very active community.

As I progress through I'll add more, but these were fun so far!

### <a href="https://leetcode.com/problems/average-time-of-process-per-machine">Average Time of Process per Machine</a>

This turned out to be a march of the CTEs! CTEs are "common table expressions", a method to define a temporary result set you can refer to later in the query. I switched to using CTEs over Subqueries when my scripts got seriously out of control & hard to read.
Each approach has a specific use case & specific advantages. If you've got a super complicated subquery you need to use a few times, executing it once in a CTE & saving for later can give you a performance boost.

I got a little carried away with the CTEs, here.. and managed to beat over 80% of the other solutions!

<img src="https://github.com/HubBry/Portfolio/blob/main/images/leetcode%20CTE.png" />

### <a href="https://leetcode.com/problems/rising-temperature">Rising Temperature</a>

I was so happy to find LEAD and LAG! I first used LEAD and LAG in 2011 (when they weren't universally available) to I explore simpler ways to compare most recent and prior aggregates. These functions became a hallmark of that work and helped usher in years of productive analytics and code that was easier to understand!

LAG fetches data from a previous row, while LEAD fetches data from a subsequent row. Both functions are very similar... so similar that they're used interchangeably, depending on the sort order!

I use these window functions at every opportunity and immediately saw their utility here, but since they were a bit out of context for the challenge, LeetCode accepted the answer but wouldn't consider it as a Soution! That's OK.

<img src="https://github.com/HubBry/Portfolio/blob/main/images/Leetcode%20lag.png" />

