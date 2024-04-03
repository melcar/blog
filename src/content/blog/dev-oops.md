---
title: Dev-Oops
description: Publishing rust documentation on git.
pubDate: Apr 3 2024
heroImage: /blog-placeholder-3.jpg
tags:
     - Rust
     - CMPRSD
     - Dev-Ops
---

Finally, the (empty) [documentation](https://cmprsd.beltus.be/doc/cmprsd/index.html) of the CMPRSD project is online! To deploy it I used the same tool as for the rest of my projects,  [github actions](https://github.com/features/actions).

Here the goal was simple. Generate the Rust documentation using 

<p style="text-align: center;">
    <code>
        cargo doc --no-deps
    </code>
</p>

and move the generated documentation to the [gh-pages](https://github.com/melcar/cmprsd/tree/gh-pages) branch. 

This is the same workflow as I use for the [benchmarks](https://cmprsd.beltus.be/dev/bench/). The difference is that for the benchmarks I use a [github action](https://github.com/benchmark-action/github-action-benchmark/tree/master) that does it automatically for me. with a very minimal setup.

My first attempt at this was to try to find a git command that would allow me to push from branch A to branch B. I was not aware of such a feature existing, and even though it is possible it pushed all the files in the current branch instead of just the documentation that I just committed. The reason is that the repository we are set in is a clone of the main branch. Therefore when pushing to the other branch from main we push all the content that is already committed in that branch.

After taking some time to read how the benchmark action for benchmark and others were doing I was happy to find such a simple trick! Instead of trying to push from one branch to another, a much simpler thing is done.
1. Copy the branch you want to locally in a new repo
2. Move the files you want to push to that repository
3. CD to that repository
4. Commit the files you want to commit and push. 

A pretty straightforward approach that delivers. 

Only one piece was missing for it to work. In the github action environment, I could pull my branch as it is public. But to push it, it is another story. Indeed I could perform a push operation from the branch that was instantiated by the github action, but in the repository I just cloned I did not have the right to do so. This is fixed by 
1.  [Generating a **P**ersonal **A**ccess **T**oken](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).
2. [Storing it as a secret for the repository](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions).
3. Using that secret in the github action script's push command <br>
<p style="test-align: center;">
    <code>
        git push "https://${{ secrets.PAT }}@github.com/melcar/cmprsd.git
    </code>
</p>

Now I can be happy that the documentation will be always up to date and readily available online, which will also be motivation for writing more of it. And I can also be happy to have gathered that knowledge as from now on I'll have the possibility to push new benchmarks, documentation, samples to the github branch page of my projects without the necessity of relying on  github action presets. 
