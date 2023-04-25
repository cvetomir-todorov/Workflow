# Introduction

* Automated code style, code quality analysis, automated testing with code coverage... are not enough
* Code reviews are essential to achieve correctness and good quality
* The process also brings the team together and helps spread team knowledge

# Checklist

Code reviews should verify the following for each PR:

* Domain goal
* Testing
* System design
* Internal design
* Performance
* Security
* Code style (in addition to automated)
* Code quality (in addition to automated)
* TODO add more

# Conflict resolution

* Code reviews means people often discuss, sometimes debate, on a rare occasion argue
* In order to minimize potential decrease in team morale, cohesion and togetherness a few helpful principles can be followed
  - Language
    - Be respectful
    - Be short, efficient, to the point
    - Avoid being excessively polite
  - When an issue is spotted refer to **the code** producing it, not the **author**
    - Every good engineer can write a piece of bad code occasionally
    - Reduces chances that author interprets the comment as an attack on how good engineer he/she is
  - Consider having a call or discuss in person
    - Differences of opinion could be because of ambiguity and/or misunderstanding
    - Communicating while seeing the other person can be a reminder of the humanitarian side of the engineering
  - Bring someone else, if it's only the author and 1 reviewer arguing
    - Outside perspective could help see missed opportunities for resolution

# Nit-picking

Nit-picking should not be avoided but rather **encouraged** and everyone should be aware of that

* We should nit-pick to improve code which in turn would improve the end result
* We should nit-pick without fear of having an argument or hurting author's feelings
* Large number of nit-picking comments should not be interpreted by the author as producing low quality code
* To point out that a comment is a nit-pick just prefix it with `Nit: `
* This way the PR author would know this comment isn't something serious
* Example: `Nit: use == instead of patterns`
