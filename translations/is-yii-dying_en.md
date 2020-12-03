Title: Is Yii Dying?
Category: Programming
Tags: Web Framework, PHP, Yii, reprinting
Authors: Paul Klimov

> Origin Url:[is yii dying][1]

> **By Paul Klimov(Former Core Developer of Yii)**: 

It is sad to realize, but indeed Yii is dying. But it has nothing to do to the number of the latest commits or outdated milestones. It also has nothing to do with the Qiang leaving the project. For the fully non-commercial open-source project such things are common enough and happens from time to time.

The real problem is Yii is very outdated technology, which does not keep up with the modern trends. The team refuses to acknowledge the fact that requirements for the modern web application has changed over latest years. They stick to the BC-keep policy too much since 2.0 release, which make Yii2 lacking of many modern approaches and features. It is ridiculous to keep support for PHP 5.4, while even 5.5 is completely dead by now and any indifferent developer switch to PHP >=7.0 for the better performance.

The team states supporting of PHP 5.4 is crucial for existing Yii-based application, while I can not see why, while installing of PHP 5.4 from regular code repository is already impossible.

While it is common requirement of the modern web project to provide “single page application” based on modern JS frameworks like ReactJS, EmberJS, VueJS and so on, Yii keeps enforcing JQuery, facilitating its usage and requiring its installation.
I have spent many efforts to persuade the team to finally move forward and make new major release. I have committed the changesets supporting PSR-3 “Logger”, PSR-16 “Simple Cache” and PSR-7 “HTTP Message”. I have provided solution for JQuery separation via dedicated optional extension. See the changelog for the full picture:[CHANGELOG][1]

I have spent much efforts to bring new major version to life, but they were in vein…
At the begging of this year the *whole* team finally agreed on the online Slack meeting to stop support of the 2.0.x and switch forces to 2.1.x (now 3.x) release. So the latest 2.0 version have to be 2.0.14. However, this agreement has been broken. The team refused to switch course. As you can see 2 minor versions were released instead: “2.0.15” and “2.0.16”, while there were no progress at “2.1” (“3.0”).
I have updated main repository code as main extensions code to make it possible to have early access to the major version. See my post about it:[yii-21-early-access][2]

This work has been complete at the March 3rd. At that time I was sure we can make at least “beta” release at the end of the May. But the team has started full scale “holy wars” around DI specification and PSR-11 interpretation.
See discussion at:[patreon.com/yii-development-19759260][3]

Even if Yii 3.0 to be released, the course, which team has take around DI and PSR-11, suggests dropping the Yii base core principle of usage array as an universal object configuration in the favor of PSR-11 DI approach, which requires constant creation of the “factory” classes, which are absolutely redundant around Yii1 or Yii2. So when the time comes for the Yii 4.0 release, it will have nothing in common with the current Yii2 architecture, and any developer using Yii will have to completely rewrite his application.

The main reason of the current state of things, to be said briefly, is the fact that the most members of the core team have no personal interest in Yii development. For example, Alexander Makarov (aka samdark) does not use Yii at his current commercial work for several years already; Carsten Brandt (aka cebe) has his own company, which operates many technologies and have many projects, but only some of them are written on Yii; Boudewijn Vahrmeijer (aka dynasource) is fully consumed with his commercial project, having no time for the framework development and so on. Only 2 members of the core team have a Yii framework as a codebase for their professional commercial projects: me (aka klimov-paul) and Dmitry Naumenko (aka Silverfire).

Despite it is a sad thing it is a normal situation. Yii is NON COMMERCIAL project. Each its core team member DOES NOT earn a single dollar for their work. Thus no one can demand them doing anything. You can not enforce people to spend their free time, gaining nothing in return. Personally I stick to this project as I use it as core base for my commercial work, so I have indirect benefit from its development. But this statement does not apply for every member of the team.

Team also relies highly on the community, expecting its member to solve own problems themselves. While having active community of the developers is priceless and huge benefit, it unfortunately can not make major release possible. Particular community member is unlikely will spend huge amount of time, which is required for the dramatic changes of the major release, risking this time will be lost in vein as the core team will not accept his pull request. The core team should make a course for the major release, create a skeleton, so community can fill the blanks around it. But it is hopeless to wait for the community to build this skeleton on its own.

You may be surprised to hear this from one of the YiiSoft core memeber, but DO NOT recommend to start new project on Yii2 or migrate project from other framework to Yii2. It would be much more reliable for you to use Laravel. It is relatively close to Yii by its architecture and approaches, while it has a commercial background and support, which make its future reliable.

But the final choice is always up to you.

**Note:**

It is also dicussed at offical forum as topic:[The future of Yii][4]

[1]:https://github.com/yiisoft/CHANGELOG "Is Yii Dying?"
[2]:https://yiifeed.com/news/366/yii-21-early-access "yii-21-early-access"
[3]:https://www.patreon.com/posts/yii-development-19759260 "patreon.com/yii-development-19759260"
[4]:https://forum.yiiframework.com/t/the-future-of-yii/124616 "The future of Yii"