---
title: "Knowledge versioning"
date: '2016-06-11T11:53:27+00:00'
wp_id: 2929
wp_status: draft
wp_type: post
---

ServiceNow brought some great features to Knowledge in version 3 that debuted with Fuji, but one feature lots of people need and that's still missing (as of Helsinki, at least) is version control. We had a team at our company that needed to introduce an approval step into their article publishing workflow, and it frustrated them that once an article was initially approved and published, anyone with the ability to edit could then make changes to the article without going through any sort of approval process.

We briefly considered forcing edited articles back into a draft status, which would solve the problem of making edits go through an approval step, but was unacceptable since it would take the article completely out of commission for however long it would take to approve the changes. We quickly concluded what we really needed was the ability to have the new version of the article in review status while the previous version of the article remained published and available to our staff and customers, which of course meant we needed version control.

Our solution turned out to be pretty elegant. In this article I'll show you exactly how we did it so you can implement this yourself in your instance.

<h2>Step 1: Fields</h2>

The first thing to do is create some new fields on the Knowledge (kb_knowledge) table.

<ul>
	<li>Label: <strong>Canonical Number</strong></li>
	<li>Name: u_canonical_number</li>
	<li>Type: String</li>
	<li>Max length: 40</li>
	<li>Default Value: javascript:current.number;</li>
</ul>

<ul>
	<li>Label: <strong>Version</strong></li>
	<li>Name: u_version</li>
	<li>Type: Integer</li>
	<li>Default Value: 1</li>
</ul>

<ul>
	<li>Label: <strong>Edit Summary</strong></li>
	<li>Name: u_edit_summary</li>
	<li>Type: String</li>
	<li>Max length: 500</li>
</ul>
