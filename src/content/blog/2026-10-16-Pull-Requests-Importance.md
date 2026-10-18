---
title: 'Pull Requests – Why Are They So Important? '
description: 'Why pull requests matter more than ever in the age of agentic coding, from code quality to team understanding.'
pubDate: 'Oct 16 2026'
heroImage: '../../assets/mac-book-coding.jpg'
tags:
  - Software Engineering
  - Code Review 
  - Pull Requests
  - Agentic Coding
---
I remember when I was a younger, less experienced software developer, feeling nervous submitting a pull request. It felt like I was being marked for an assignment. Now I am in a senior position I know that premise was wrong. Pull requests are more about collaboration, learning than just being corrected. 

With the new age of agentic coding coming through I think it is important to look at practices as software engineers and reflect what is still important which I would argue pull requests have now become even more important. Why do I say this? 

## Why Do We Do Pull Requests? 

The importance of pull requests is more than picking up on bugs before they get to production. It is also a great way of keeping code to a specific standard. Of course, not this is not the only way to keep coding standards, you still need linters and style configs set up. The other side of it is having a team-wide understanding of the code base, a way of knowledge sharing and having context of what is happening with new features or bug fixes. I see this as being more and more important, as code is being produced by agents. As a team you need to be responsible for the code base and understand the code that has been produced.  

## What Makes a Good Review? 

What should the reviewer get out of it and what about the submitter? I feel like any reviewer should be able to walk away after doing a review with the understanding on what changes have been made, why they have been made, and what impact that change will have. Although depending on the person's level and experience with the project the impact may not be fully understood.   

For the submitter, they shouldn’t feel nervous about the review; they should take the feedback as an opportunity to grow and learn more about this craft. Or update the instruction for the agent they used. 

 A practice I do is tagging my reviews with `Required` | `Suggestion` | `Question` | `Nitpick`. This helps the submitter know the priority of the feedback and what needs to change and what is a personal preference.  Being direct and clear in the feedback is also important, saying things like “I wonder if we did it this way....” doesn’t tell the submitter if you want the change, asking a question or suggesting something different. A better example would be “This should be done this way” when required or “Another way this could be done is this way” with the suggestion tag.  Although there is another train of thought, and for some people it is better to ask questions on why they have done it the way they have, I personally have found that depends on who you are reviewing. Some prefer their assumptions to be questions; others appreciate directness so they can get their job done. 

When someone approaches a pull request and just checks whether the tests have passed before clicking approve, they have missed an opportunity to understand how the code base is changing and the possibility of learning something new. 

## How Is Agentic Coding Changing Pull Requests? 

Now back to AI. More agents are producing the code and reviewing that code. Most of the time the code works fine. The issue I have seen is the maintainability of that code. For example, duplicated code and new unnecessary files. Code reviews done by a human give that opportunity to revise the instructions and rules agents should follow and update the human reviewer on the code base (yes, I am shouting that). At the end of the day as the software team, we are the ones responsible for what the agents produced, no different as if it was a human implementing the code. 

## What Makes a Good Pull Request? 

Starting with the team, document what should be looked for in a pull request review. This helps junior and less experienced developers perform review. It also helps create coding standards for agents to follow.  

Every senior software engineer will yell “keep it small”. We have all been there, looking at a large pull request because of a new feature. Accepting that mistakes will go through but trying your best to give constructive feedback. Having them too small can also be difficult because you can lose context of the whole code base. A good pull request should be a sufficient update, not a particular size but a coherent change.  The description should be clear on what you have changed and there should be a link to the feature or bug ticket. 

## Practical Tips on How I Perform a Review 

I first prefer to look at the code diff myself. This is so I can understand the change before seeing it run, or an agent opinion on it.  As I review, I add any feedback along the way. 

I will then use an agent to review, asking very pointed questions. I take what it returns with a grain of salt. I have found agents are keen to please and want to give you an answer. But I have picked up issues I would have missed otherwise. Again, adding the feedback as it comes through.   
 
Finally I run the application and try to break it. If anything looks unexpected or behaves oddly this is when I will let the submitter know. 

If the code has been produced by an agent, I will also use this opportunity to revise the standards expected of the agent. 

## Pull Requests Are About More Than Approval 

Overall, even in the world of agentic coding, I don’t see reviews going away anytime soon. They have already started to look different, with agents being part of the review process. But completely removing the human will be a great disservice to the team's knowledge and the future of the system. Pull requests are one of the tools for engineers to understand the code base they are part of developing.  