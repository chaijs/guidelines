## Supported Cycle

To ensure a consistent level of compatibility & support in our projects, each project under the Chai organisations must strictly adhere to a standardised lifecycle support policy, and platform support policy, as document below.

### Supported Lifecycle

We can only provide support for the latest version of any of our projects. As soon as a new release of any project is made, older versions of that project are considered end-of-life. We will not actively support older versions unless a negotiation with a third party has been made. Any actively supported older versions will be documented in the respective projects readme file.

### Supported Platforms

#### Node.js

We support Node.js, following its LTS policy. [Node.js' release cycle is documented here](https://github.com/nodejs/LTS#release-schedule1) - which can be effectively summarised as: even numbered versions (4, 6, 8, 10) are supported from their date of release for around 3 years, while odd versions (5, 7, 9, 11) are supported for around 6 months. We follow this support cycle by supporting everything from the oldest release still in Maintainence to the current release. Any version that is marked *"End of Life"* we do not officially support, but we will continue to support any version marked as *"Maintainence"* or *"Active"*.

##### Validating Node.js Support

We validate our support for Node.js by running Continuous Integration testing our projects in the latest release of every major version - for example at the time of writing the current LTS release version is `6.11.13`; we will test this version but none of the earlier releases in the 6.0 branch.

#### Firefox

We support Firefox from it's _Extended Support Release_ (ESR) up until the _latest_ released version. [Firefox's ESR release cycle is documented here](https://www.mozilla.org/en-US/firefox/organizations/faq/) and can be effectively summarised as: a new ESR release is made approximately every year, while new regular releases are made every 6 weeks. For us this means we essentially support a years worth of Firefox releases.

##### Validating Firefox Support

We validate our support for Node.js by running Continuous Integration testing our projects in both the latest ESR of Firefox, as well as the latest version of Firefox. Any versions inbetween are not tested as it is unlikely that there will be failures in specific versions between the ESR and latest releases that aren't reflected in one or the other.

#### Chrome

Chrome has no Extended or Long Term Support cycle, and as such only the latest version so Chrome is officially supported by Google. We provide soft-support for Chrome releases up to a year old (that is, while we do not test any older releases, if a user finds a bug we will fix it).

##### Validating Chrome support

We validate our support for Chrome by running Continuous Integration testing for the latest version of Chrome. Older versions aren't tested because this is not easily available in our Continuous Integration environments.

#### Safari (MacOS and iOS)

Safari is tied to the MacOS and iOS operating system releases, of which Apple supports the last 3 releases in each (this equates to roughly 3 years, as a new MacOS and iOS release is made every year), however Apple also releases updates for Safari versions for the last 3 _desktop_ operating system versions. [Apple's support notes for security releases can be found here](https://support.apple.com/en-us/HT201222). Information around Safari releases can be a little tricky to find, and Apple does not have sufficient support documentation around this - the best place to find this information is on the [Wikipedia entry for Safari version history](https://en.wikipedia.org/wiki/Safari_version_history). To demonstrate how the release cycle works; iOS 8 and MacOS 10.10 both shipped with Safari 8, iOS9 and MacOS 10.11 shipped with Safari 9, iOS10 and MacOS 10.12 shipped Safari 10 and iOS11 and MacOS 10.13 shipped with Safari 11. Safari 10 was backported as an update to MacOS 10.11 and 10.10 users, as was Safari 11 to MacOS 10.12 and 10.11 users. The iOS version of Safari remains fixed.

##### Validating Safari support

We validate Safari support by running Continuous Integration testing for the oldest supported version of iOS and MacOS, as well as the latest supported versions of both. Any versions inbetween are not tested as it is unlikely that there will be failures in specific versions between the oldest supported version and the latest release that aren't reflected in one or the other.

#### Edge

Microsoft have no documentation of the Microsoft Edge Support Cycle. We currently support the latest release of Microsoft Edge, with soft-support for public up to a year old (that is, we do not test older releases, but if a user finds a bug we will fix it).

##### Validating Edge support

We validate support of Edge by running Continuous Integration testing for the latest version. Older versions aren't tested due to build time constraints.

#### Internet Explorer

[Microsoft have officially stopped support for Internet Explorer 10 and below since January 2016](https://www.microsoft.com/en-gb/windowsforbusiness/end-of-ie-support), but still continue to support Internet Explorer 11 in Windows 7, 8 and 10. The end-of-life date for Windows 10 is October 25 as explained in the [Microsoft LifeCycle Fact sheet](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet), and so we can expect to support Internet Explorer 11 until then. We do not support older versions of Internet Explorer.

##### Validating Internet Explorer support

We validate support of Internet Explorer 11 by running Continuous Integration testing for it. 

#### Opera, Maxthon, Camino, Konqueror, OmniWeb, <Insert Browser Here>

We do not support any of these browsers officially, this is because their usage is too small or because they use the same JS/HTML engines as already supported engines.

#### Rhino JS, Node ChakraCore, <Insert Server Side Engine Here>

We only officially support Node.js. The usage share of alternative engines is too small for us to consider supporting them.

### Questions

#### What if I want support of an older version of a project?

If you are using an older version of one of the Chai projects - for example Chai@3.5.0 - and wish for us to backport fixes, this can be negotiated with the team for that project. The team responsible for the maintainance of the project will provide a cost breakdown of the engineering time it would require to backport any bugfixes to older versions and make a release which would need to be paid upfront for the work to commence. For example if you wanted a bugfix from chai@4.1.1 backported to chai@3.5.0, we would estimate the number of days it would take 1 maintainer to make this fix, and multiply it by the going market day rate, in US$. You should fully expect this cost to be in thousands-of-dollars cost region. Please note any work paid for to backport features will be made open source, and as such all users will benefit from this.

All of our projects are open source, and so if you disagree with the pricing we quote you, you are of course welcome to solicit other developers to make the neccessary changes and raise a pull request.

#### What if I want a project to support an older platform?

If you would like the latest version of a project to support an older platform, for example Chai@4 to support IE9 - and you wish for us to maintain this, then this can be negotiated with the team for that project. The team responsible for the maintainance of the project will provide a cost breakdown of the engineering time it would require to change the project's code to support the older platform which would need to be paid upfront for the work to commence. Additional on-going costs will incur for continuing to support the older platform for the duration of the major version of that project. For example if you wanted a chai@4 to support IE9, we would estimate the number of days it would take 1 maintainer to make the necessary code changes and multiply by the going market day rate, in US$, as well as estimate a monthly retainer (some amount of days multiplied by the market day rate in US$) in order to continue support until Chai@5 was released. The on-going cost would need to be made regularly to ensure we are able to continue to support the older platform. You should fully expect this cost to be in tens-of-thousands-of-dollars cost region. Please note any work paid for to support additional platforms will be made open source, and as such all users will benefit from this.

#### How do we justify charging for out-of-cycle support?

This is an open source project, where all of the maintainers or contributors are working on this during free time, or company-sponsored time. Existing support has effectively been paid for by the donation of time from the maintainers, or by existing company sponsorhip. Out-of-cycle support requires additional work by the project maintainers, that time needs to be paid for somehow.

#### What if I find a bug in a supported engine or browser?

If you are using the latest version of a chai project, and find a bug in a version we claim to support, then please raise a bug in the issue tracker for that project. It is likely that a patch-release will be made to fix this bug, where possible.
