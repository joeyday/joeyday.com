---
title: "Closing SLA Loopholes"
date: '2015-08-06T15:09:16+00:00'
wp_id: 2818
wp_status: draft
wp_type: post
---

<img src="http://joeyday.com/wp-content/uploads/2015/08/clock-1024x1024.jpg" alt="Clock" width="200" class="alignleft size-large wp-image-2831" /> So, the out-of-box ServiceNow SLA Engine is a little wonky. Let me explain what I mean. Take the out-of-box Incident priority SLAs as examples. They have start conditions based on the priority and stop conditions based on Incident state. Makes total sense. If I mark a ticket as priority 1, ServiceNow starts a clock ticking. When I later resolve the Incident, ServiceNow stops that clock and tells me whether I came in under or over some predetermined deadline. If, before resolving the Incident, I re-prioritize itâ€”say I change it from a P3 to a P2â€”the SLA related to the previous priority gets cancelled and a new SLA related to the new priority gets created and backdated to when the ticket came in. So far so good.

Let's do something a little more complicated, though not at all out of the ordinary. If I change the priority on a ticket and resolve it <em>at the same time</em> (i.e. with a single save or submit operation)â€”say I change priority from P3 to P2, set the status to Resolved, then click Saveâ€”a very strange thing happens: the SLA for the previous priority (which really ought to be cancelled) gets marked as completed and achieved, and an SLA for the new priority is never created (!). What if we came in under the P3 SLA but breached the P2 SLA? Out of the box, ServiceNow records it as though we came in under SLA and no one is the wiser.

<h2>Wut?!</h2>

What's going on here? What I've discovered is two SLA loopholes acting in concert to create this bad situation:
<ol>
	<li>When both the start and stop conditions for an SLA are satisfied, the out-of-box SLA Condition Rules say the SLA should not be created.</li>
	<li>When the stop conditions for an SLA are satisfied, the out-of-box SLA Condition Rules say the SLA should be marked as achieved, regardless of whether the start conditions still hold.</li>
</ol>

These two loopholes together are responsible for the scenario I described above, but, working together or alone, they can cause other strange SLA behavior.

Say you have an SLA to track a first response on a ticket. Maybe you have an Incident state of â€œNewâ€ and you have an SLA to get every new Incident into an â€œOpenâ€ or â€œAssignedâ€ or â€œIn Progressâ€ state within, say, four hours. So you set up an SLA with the start condition of State != Resolved and stop condition of State != New. Now all new tickets coming in will start this clock ticking until the state moves from New to In Progress. Except, what if someone creates a new Incident and sets the state to In Progress right off the bat? Technically, the first response SLA was achieved, right? But because of loophole #1 above, acting all by itself, the SLA won't be created because both the start and stop conditions were satisfied at the same time.

That may not seem like a serious situation, so let me up the ante a little. This scenario is admittedly a little contrived, but we do have a setup very similar to this for one of the task record types where I work. Say you have an â€œopenedâ€ date on your Incident table that can be filled in by your technicians and you set your SLAs to all be retroactive to that date. Then say a voice mail or a fax comes in and nobody's able to act on it right away. A few days later a technician listens to the voice mail or reads the fax and finally fixes the issue. When the technician opens the Incident record, they do what they're supposed to do and set the opened date to three days ago when they got the voice mail or fax and, at the same time (in a single save operation), they set the priority to P1 and set the state to Resolved. Technically, though they breached the P1 SLA, because the start and stop conditions for the SLA have been satisfied at the same time, no SLA record is generated, and the fact that SLA was breached never shows up on any SLA report.

Okay, so what sort of situations can be brought up by loophole #2 acting by itself? Say I have a bunch of CI-based SLAs set up, and maybe some CIs have SLAs defined (like 3 days for e-mail issues) but others don't (like database). Now say a ticket comes in and I mark it as an e-mail issue, but as I'm closing the ticket, I realize it's not really an e-mail issue, but a database issue. If I correct the CI field and close the ticket in a single save operation, because of loophole #2, my e-mail SLA will get completed (and breached or achieved, depending on whether I resolved the Incident within the SLA) even though in the end the ticket is no longer marked as an e-mail-related issue. So later on somebody reviewing SLA records might wonder why we're not fixing some e-mail issues in a timely enough manner, when really this Incident had nothing to do with e-mail at all.

Okay, hopefully by now I've convinced you this is a serious situation and needs fixing. Fear not, I strive never to bring up a problem without proposing a solution, so here it is.



By the way, this will seriously mess up any SLAs you have with a start condition of active = true. If you're going to do this, Test the crap out of your SLAs in a sub-prod instance before going to production (but you always do that, right? Right?).


Modifying SLA Condition Rules: https://wiki.servicenow.com/index.php?title=Modifying_SLA_Condition_Rules

SLA Loopholes: https://community.servicenow.com/message/692373#692373

SLA's Not Working As Expected: https://community.servicenow.com/message/717390#717390
