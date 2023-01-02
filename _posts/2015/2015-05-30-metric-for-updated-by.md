---
id: 2773
title: 'Metric for Updated By'
date: '2015-05-30T00:33:41+00:00'
author: Joey
layout: post
guid: 'http://joeyday.com/?p=2773'
subtitle: 'Defining a ServiceNow Metric to track every update to any record in a table'
dsq_thread_id:
    - '3806063223'
categories:
    - essay
tags:
    - 'business rule'
    - metric
    - servicenow
    - sys_updated_by
---

A friend recently asked how he could create a ServiceNow Metric that would track who makes each and every update to records in a given table. Sounds easy enough, right?

Well, it turns out the only fields that would make sense to trigger such a metric are system fields like *sys_updated_on* or *sys_updated_by*, and the tricky thing is those fields don’t get monitored by default for calculating metrics. I searched the ServiceNow Community and found a way to do it, and below I am providing an off-the-shelf Metric Definition and Business Rule that will track every time a record is updated on a table. ((I’m indebted to this Community thread that gave me the working solution to the dilemma: *[ServiceNow Community › Metric definition for sys\_updated\_by](https://community.servicenow.com/thread/165157 "ServiceNow Community › Metric definition for sys_updated_by")*.))

## The Metric Definition

I’ve defined this for the Task table (which works for any tables extended from Task), but you’re of course welcome to make it more specific as your needs require.

**Name:** Task Updated By
**Table:** Task [task]
**Field:** Updated by
**Type:** Script calculation

**Script:**
{% highlight javascript %}
createMetric(current.sys_updated_by.toString());

function createMetric(value) {
	var mi = new MetricInstance(definition, current);
	var gr = mi.getNewRecord();
	gr.field_value = value;
	gr.calculation_complete = true;
	gr.insert();
}
{% endhighlight %}

## The Business Rule

This is the secret sauce. Since fields like *sys_updated_by* aren’t monitored for metric calculations, we need to explicitly declare that we want it monitored by setting up a Business Rule to fire the same event that would normally be fired for non-system fields.

**Name:** Metric Event for Updated By
**Table:** Task [task]
**Advanced:** true
**When:** after
**Insert:** true
**Update:** true

**Script:**
{% highlight javascript %}
function onAfter(current, previous) {
	gs.eventQueue('metric.update', current, '[sys_updated_by]', 1, 'metric_update');
}
{% endhighlight %}

That’s all there is to it. Now any time someone inserts or updates any Task (or records in whatever table you specified instead) you’ll get a new Metric Instance with a value containing that User’s user name.{% include endmark.html %}