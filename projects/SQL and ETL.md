# SQL and ETL Examples

I've been surprised at the robustness of the <a href="https://leetcode.com/">LeetCode platform</a>, and I've got a few examples of the <a href="https://leetcode.com/studyplan/top-sql-50/">SQL 50!</a>

## SQL 50

The SQL 50 is a great collection of challenges that require skill in applying basic joins, select statements, aggregate functions, subqueries, strings... with a whiole host of solutions and guidance available from the very active community.

As I progress through I'll add more, but these were fun so far!

### <a href="https://leetcode.com/problems/average-time-of-process-per-machine">Average Time of Process per Machine</a>

This turned out to be a march of the CTEs! CTEs a re "common table expressions" is a method to define a temporary result set you can refer to later in the query. I switched to using CTEs over Subqueries when my scripts got seriously out of control & hard to read.
Each approach has a specific use case & specific advantages. If you've got a super complicated subquery you need to use a few times, executing it once in a CTE & saving for later can give you a performance boost.

I got a little carried away with the CTEs, here.. and managed to beat over 80% of the other solutions!

<img src="https://github.com/HubBry/Portfolio/blob/main/images/leetcode%20CTE.png" />

My solution:
/* Write your T-SQL query statement below */
with mach_end as
(select machine_id, process_id, [timestamp] as time_e from Activity where activity_type='end'
--and machine_id=0
)

,mach_start as
(select machine_id, process_id, [timestamp] as time_s from Activity where activity_type='start'
--and machine_id=0
)

,base_table as
(
select
e.machine_id
,e.process_id
,time_e-time_s as process_time

from mach_end e left outer join mach_start s on e.machine_id=s.machine_id and e.process_id=s.process_id
)

,presummary as
(
select
machine_id
,count(process_id) as processes
,sum(process_time) as P_time

from base_table

group by machine_id
)

select machine_id, round((P_time/processes), 3) as processing_time from presummary
