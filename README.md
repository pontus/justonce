# justonce

Simple output handler to suppress multiple mails from similar runs with cron

# Motivation

Running a lot of services that normally are silent but sometimes starts spawning a lot of output from cron 

There are a lot of other cron wrappers out there, possibly solving this problem as well. As far as I could understand, none of the ones I looked at did though, so it seemed simpler to just roll another one. 

# Prerequisites

This should work with most modern UN*Xes. 

Please check that the script have read and execute permissions and is accessible for the user that will be running it, though.

# Usage

Assuming you have a cron that allows shell segments (you probably do!), just stick a redirection and a pipe to justonce at the end of commands for cron entries that are sometimes chatty, like so:

*/5 * * * * flock -n /tmp/toolrunlock /usr/local/bin/produceoutputsometimes 2>&1   | /usr/local/bin/justonce

I recommend redirection of stderr as well as explicitly pointing out the path.
