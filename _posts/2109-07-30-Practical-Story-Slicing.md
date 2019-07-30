---
layout: post
title:  "Practical Story Slicing with Neil Killick"
date:   2019-07-30 11:16:45 +1000
categories: story slicing agile
---

This post is a summary of Practical Story Slicing, a half day course run by Niel Killick in Melbourne, Australia. I attended this course in 2018, previously this post was hosted on an internal company blog, I felt it was worth exposing to the world. 

### What even am story?
We define stories as both adding some new capability for a user/customer or making some change that enables that new capability. In this way
we incorporate things like refactor stories / enablers that don’t have a clear human at the end waiting for their tasty, tasty value.
We were careful not to get caught up in language throughout this process, a story is a story is a story, turtles all the way down. Epics are just big
stories, begging to be taken to with our sharpened axe. Part of the intention here is to develop methods for exploring the problem space.

### Motivation:
#### Why bother splitting a story?
There are a bunch of reasons we might split a story, including but not limited to: 
- deliver value to the customer faster.
- lower the risk associated with a story.
- make a story easier to test.
- tighten the feedback loop on new work.
- show demonstrable progress.
- create a shared understanding of the problem space.

### How do we split?
We have three levels at which we can slice depending on where in our iteration we are.

#### Capability Slicing
--- 
Capability Slicing is a process of analysis at a customer level in order to explore the problem space represented by an story statement.
For example, take the statement below:
> Enable Acme Bank customers to bank with us online

##### Seams
To start the process of unpicking this we can identify seams within the statement that represent general terms. We can take those generalities
and make them more specific to entities in our domain, substituting them back into the original statement to generate a slice.  

In this example we can identify three seams:
> Enable Acme Bank **customers** to **bank** with us **online**

We undertake an enumeration exercise to explore more specific examples of what these general terms represent. Keep in mind this is an
exercise in problem space exploration, not a concrete exercise in the generation of stories. We will apply a level of analysis and pragmatism to
decide which of these actually becomes a backlog item. 

| Customers | Bank | Online |
|---|---|---|
| Personal | pay bills | web / browser |
| Groups| transfer| mobile |
| Business| get paid| Family |
| check balance| Trusts| bank money |
| Government| set up auto payments| Charities |

We can then substitute these more specific terms back into the original story description:
> Enable Acme Bank **personal customers** to **pay bills** in the **browser**

By undertaking another level of enumeration we generate, in this case, 84 candidate stories. While this may seem extreme we must keep in mind
that not all of these will be viable stories, the real value in this process is exploration of the problem space

#### Functional Slicing
---
Functional slicing encompasses more of a design focus, while still keeping a high level view and operating from the perspective of the user. We
look to identify user workflows in the context of the given story, identifying the simplest possible workflow and identifying incrementally more
complex options to make it shippable.
This is an activity that may be undertaken at backlog grooming and or sprint planning in order to further flesh out a story and generate conversations on any details and information that might be required.

A nice practical application of this usually involves a bunch of post-its (how unusual) and the team gathered around a wall. I will try and construct
an analog experience here using poorly constructed diagrams and magic.
If we were to select one of the stories generated during the previous capability exercise we see that while we found more specific terms to clarify
generalities, there is still a lot of information we don’t have.

As an exercise let’s the following story and apply functional slicing to it:

> Enable Acme Bank personal customers to pay a bill with us via the website

We want to identify the simplest customer workflow for this story (blue boxes), we focus on the actual actions a customer might carry out in order
to achieve this (orange boxes):

{% mermaid %}
  graph LR
  A-->B
{% endmermaid %}

Notice in some cases the simplest possible action is no action.
Let’s take the Select Biller step and dig down into some of the other options available to us, again moving the simplest approach to more
complex solutions.

We might make a solution based on time to market, value to stakeholders, regulatory requirements or any number of other concerns. In some
cases it is worth noting the the simplest solution is in fact doing nothing or the absence of a particular step, depending on context.

#### Technical Slicing
---
Technical slicing is a process that should be undertaken during sprint planning. In contrast to the previous methods this is focussed on the
technical steps needed to deliver a solution, a vertical slice through the story. Some teams may call this tasking a change, though there is a subtle
difference in the application.  

Here we will use The Hamburger Method, which is not only delicious but relevant to most peoples interests. The intention is to ensure we get a full
bite of the burger, a fully realised solution that delivers value to the stakeholder. We first identify at a high level the steps that are required, this is
analogous to tasks. We then express those steps as an implementation step required to deliver the solution, starting with the simplest possible
option. As we did with functional slicing we then enumerate any other more complex options for each of those implementation steps.
For this example we will use the following story:

> Contact dormant personal customers via email

For the sake of everyone involved I’ll refrain from trying to draw a hamburger here, use your imagination M8s.

| Vertical Slice | Simple Path | Complexity => ||||
|---|---|---|---|---|---|
| Query DB | Manual Query | Auto Query | Nightly Job ||
| Send Email| Manual Send| Auto Send Generic Email| Auto Send Personalised Email| 3rd Party Intergration
| Get Delivery Report | No Report | Txt Import | Realtime Queue | 3rd Party Integration |
| Remove Bounced| No Removal| Manual Removal| Txt Import| Realtime Queue| 3rd Party Integration |
|Mark Contacted |Manual |Txt Import |Realtime Queue |3rd Party Intergration |

After we have this map of options, we can select based on whatever concerns and considerations are appropriate, a path through thesesteps. In some cases we may get a more complex option for free or the simplest is the only viable option.

#### Summary
---

We have examined a set of methods we can apply when slicing or mapping stories, each method is best used at differing points in the development lifecycle.  

Capability Slicing might be best employed when mapping out epics and generating stories, for example if you were planning out a three month period of work in advance, or something, or whatevers. We use capability slicing when examining epics / stories at a high level, using seams to identify areas where we can be more specific and generate finer grained stories.  

Functional Slicing might be best used at backlog grooming in order to inform what further information or context you need to deliver a story. That
being said it may also be useful in Sprint Planning. We use functional slicing to explore the problem space of a particular story, shedding light on
some of the workflows a user might be expected to undertake.  

Technical Slicing is something best used just in time, at the point where we have the most information we can about a story, at Sprint Planning
perhaps. We use technical slicing to examine vertical slices of a story in order to map out what our technical approach might look like.
It is important to remember none of this is prescriptive, the intention is to highlight areas in which we might benefit from a more structured and
strategic approach.  

Take what you need, what is useful and leave the rest!  

That’s my picture. Better living everybody. 

