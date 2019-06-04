## Supported Cycle

To ensure a consistent level of compatibility & support in our projects, each project under the Chai organisation must strictly adhere to a standardised lifecycle support policy, and platform support policy, as documented below.

### Supported Lifecycle

We can only provide support for the latest version of any of our projects. As soon as a new release of any project is made, older versions of that project are considered end-of-life. We will not actively support older versions unless a negotiation with a third party has been made. Any actively supported older versions will be documented in the respective projects readme file.

### Supported Platforms

#### Node.js

We support Node.js, following its LTS policy. [Node.js' release cycle is documented here](https://nodejs.org/en/about/releases/) - which can be effectively summarised as: even numbered versions (8, 10, 12, 14) are supported from their date of release for around 3 years, while odd versions (9, 11, 13, 15) are supported for around 6 months. We follow this support cycle by supporting everything from the oldest release still in Maintainence to the current release. Any version that is marked *"End of Life"* we do not officially support, but we will continue to support any version marked as *"Maintainence"* or *"Active"*.

##### Validating Node.js Support

We validate our support for Node.js by running Continuous Integration testing our projects in the latest release of every major version - for example at the time of writing the current LTS release version is `10.16.0`; we will test this version but none of the earlier releases in the 10.x.x branch.

##### What does this look like?

The following predicts our support cycle until 2023. This is an estimate and may change based on the [Node.js release cycle](https://nodejs.org/en/about/releases/).

 - We will always have hard support for the latest version
 - As of 2019-04-01 the oldest supported version is v8
 - Node.js 8 will be supported between 2017-05-30 to around 2019-12-31
 - Node.js 9 will be supported between around 2018-04-01 to around 2019-12-31
 - Node.js 10 will be supported between around 2018-04-24 to around 2021-04-01
 - Node.js 11 will be supported between around 2019-10-23 to around 2019-06-30
 - Node.js 12 will be supported between around 2019-04-23 to around 2022-04-01
 - Node.js 13 will be supported between around 2019-10-22 to around 2020-06-01
 - After 2019-12-31 v8 will no longer be supported and the oldest supported version will be v10
 - Node.js 14 will be supported between around 2020-04-23 to around 2023-04-01
 - After 2020-06-01 v13 will no longer be supported, but v10 and v12 will continue to be supported
 - Node.js 15 will be supported between around 2020-10-23 to around 2021-06-01
 - After 2021-04-01 v10 will no longer be supported and the oldest supported version will be v12
 - Node.js 16 will be supported between around 2021-04-23 to around 2023-10-01
 - After 2021-06-01 v15 will no longe be supported, but v12 and v14 will continue to be supported
 - Node.js 17 will be supported between around 2021-10-23 to around 2022-06-01
 - After 2022-04-01 v12 will no longer be supported and the oldest supported version will be v14

#### Firefox

We support Firefox from it's _Extended Support Release_ (ESR) up until the _latest_ released version. [Firefox's ESR release cycle is documented here](https://www.mozilla.org/en-US/firefox/organizations/faq/) and can be effectively summarised as: a new ESR release is made approximately every year, while new regular releases are made every 6 weeks. For us this means we essentially support a years worth of Firefox releases.

##### Validating Firefox Support

We validate our support for Node.js by running Continuous Integration testing our projects in both the latest ESR of Firefox, as well as the latest version of Firefox. Any versions inbetween are not tested as it is unlikely that there will be failures in specific versions between the ESR and latest releases that aren't reflected in one or the other.

##### What does this look like?

The following predicts our support cycle until 2023. This is an estimate and may change based on the Firefox release cycle.

 - We will always have hard support for the latest version
 - Firefox ESR 60 will be supported between 2018-04-09 to around 2019-10-23
 - All versions of Firefox between ESR 60 to 67 will be supported until around 2019-10-23
 - Firefox ESR 68 will be supported between around 2019-07-01 to around 2020-10-23
 - After around 2019-10-23 the oldest supported version will be 68 ESR
 - All versions of Firefox between ESR 68 to 76 will be supported until around 2020-06-01
 - Firefox ESR 84 will be supported between around 2019-09-01 to around 2021-12-01
 - After around 2020-10-23 the oldest supported version will be 84 ESR
 - All versions of Firefox between ESR 84 to 92 will be supported until around 2023-03-01
 - Firefox ESR 92 will be supported between around 2021-12-01 to around 2023-03-01
 - After around 2021-12-01 the oldest supported version will be 92 ESR
 
#### Chrome

Chrome has no Extended or Long Term Support cycle, and as such only the latest version of Chrome is officially supported by Google. We provide soft-support for Chrome releases up to a year old (that is, while we do not test any older releases, if a user finds a bug we will fix it).

##### Validating Chrome support

We validate our support for Chrome by running Continuous Integration testing for the latest version of Chrome. Older versions aren't tested because this is not easily available in our Continuous Integration environments.

##### What does this look like?

The following predicts our support cycle until 2021. This is an estimate and may change based on the Chrome release cycle.

 - We will always have hard support for the latest version
 - Chrome 68 (released 2018-07-24) will receive soft-support until around 2019-07-01
 - Chrome 69 (released 2018-09-04) will receive soft-support until around 2019-09-01
 - Chrome 70 (released 2018-10-16) will receive soft-support until around 2019-10-01
 - Chrome 71 (released 2018-12-04) will receive soft-support until around 2019-12-01
 - Chrome 72 (released 2019-01-29) will receive soft-support until around 2020-01-01
 - Chrome 73 (released 2019-03-12) will receive soft-support until around 2020-03-01
 - Chrome 74 (released 2019-04-23) will receive soft-support until around 2020-04-01
 - Chrome 75 (estimated release 2019-06-04) will receive soft-support until around 2020-06-01
 - Chrome 76 (estimated release 2019-07-12) will receive soft-support until around 2020-07-01
 - Chrome 77 (estimated release 2019-08-27) will receive soft-support until around 2020-08-01
 - Chrome 78 (estimated release 2019-10-08) will receive soft-support until around 2020-10-01
 - Chrome 79 (estimated release 2019-11-19) will receive soft-support until around 2020-11-01
 

#### Safari (MacOS and iOS)

Safari is tied to the MacOS and iOS operating system releases, of which Apple supports the last 3 releases (current -2) in each (this equates to roughly 3 years, as a new MacOS and iOS release is made every year), however Apple also releases updates for Safari versions for the last 3 _desktop_ operating system versions. [Apple's support notes for security releases can be found here](https://support.apple.com/en-us/HT201222). Information around Safari releases can be a little tricky to find, and Apple does not have sufficient support documentation around this - the best place to find this information is on the [Wikipedia entry for Safari version history](https://en.wikipedia.org/wiki/Safari_version_history). To demonstrate how the release cycle works; iOS 8 and MacOS 10.10 both shipped with Safari 8, iOS9 and MacOS 10.11 shipped with Safari 9, iOS10 and MacOS 10.12 shipped Safari 10 and iOS11 and MacOS 10.13 shipped with Safari 11. Safari 10 was backported as an update to MacOS 10.11 and 10.10 users, as was Safari 11 to MacOS 10.12 and 10.11 users. The iOS version of Safari remains fixed. Essentially this means we will continue to support 3 years worth of Safari releases.

##### Validating Safari support

We validate Safari support by running Continuous Integration testing for the oldest supported version of iOS and MacOS, as well as the latest supported versions of both. Any versions inbetween are not tested as it is unlikely that there will be failures in specific versions between the oldest supported version and the latest release that aren't reflected in one or the other.

##### What does this look like?

The following predicts our support cycle until 2023. This is an estimate and may change based on the Safari release cycle.

 - We will always have hard support for the latest version
 - As of 2018-09-20 the oldest supported version of Safari is v10
 - Safari 11 (released 2017-09-19) will receive support until around 2021-09-20
 - Safari 12 (released 2018-09-17) will receive support until around 2022-09-20
 - Safari 13 (estimated release 2020-09-20) will receive support until around 2023-09-20
 - As of 2020-09-20 the oldest supported version of Safari will be v11
 - Safari 14 (estimated release 2021-09-20) will receive support until around 2024-09-20
 - As of 2021-09-20 the oldest supported version of Safari will be v12
 - Safari 15 (estimated release 2022-09-20) will receive support until around 2025-09-20
 - As of 2022-09-20 the oldest supported version of Safari will be v13
 - Safari 16 (estimated release 2023-09-20) will receive support until around 2026-09-20
 - As of 2023-09-20 the oldest supported version of Safari will be v14

#### Edge

Microsoft have no documentation of the Microsoft Edge Support Cycle. As of writing Edge 18 is the latest and final version of EdgeHTML to be released, with Microsoft moving to a Chromium based Edge browser arriving late 2019. There is no information about the release cadence of a Chromium based Edge, although it is expected to coincide with Chrome releases. As such we will support all Edge versions with the same support cycle as Chrome; supporting the latest release of Microsoft Edge, with soft-support for public releases up to a year old (that is, we do not test older releases, but if a user finds a bug we will fix it).

##### Validating Edge support

We validate support of Edge by running Continuous Integration testing for the latest version. Older versions aren't tested due to build time constraints.

##### What does this look like?

The following predicts our support cycle until 2020. This is an estimate and may change based on the Edge release cycle.

 - We will always have hard support for the latest version
 - As of 2019-04-30 the latest supported version of Edge is v18
 - Edge 18 will receive soft-support until around 2019-11-01
 - As of 2019-11-01 EdgeHTML will no longer be supported, and only Chromium versions of Edge will be supported.
 - Edge 76 (estimated release 2019-10-01) will be supported until around 2020-10-01

#### Internet Explorer

[Microsoft have officially stopped support for Internet Explorer 10 and below since January 2016](https://www.microsoft.com/en-gb/windowsforbusiness/end-of-ie-support), but still continue to support Internet Explorer 11 in Windows 7, 8 and 10. The end-of-life date for Windows 10 is 2025-10-14 as explained in the [Microsoft LifeCycle Fact sheet](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet), and so we can expect to support Internet Explorer 11 until then. We do not support older versions of Internet Explorer.

##### Validating Internet Explorer support

We validate support of Internet Explorer 11 by running Continuous Integration testing for it. 

##### What does this look like?

 - We do not support IE10 or below
 - We will support IE11 until around 2025-10-14

#### Opera, Maxthon, Camino, Konqueror, OmniWeb, <Insert Browser Here>

We do not support any of these browsers officially, this is because their usage is too small or because they use the same JS/HTML engines as already supported engines.

#### Rhino JS, Node ChakraCore, <Insert Server Side Engine Here>

We only officially support Node.js. The usage share of alternative engines is too small for us to consider supporting them.

### Questions

#### What if I want support of an older version of a project?

If you are using an older version of one of the Chai projects - for example Chai@3.5.0 - we would strongly recommend upgrading to the latest version. If that is not possible, then you may consider filing an issue about backporting bugfixes or features to older versions of the project in question. We will consider these requests on a case per case basis.

#### What if I want a project to support an older platform?

If you would like the latest version of a project to support an older platform, for example Chai@4 to support IE9 - then you may consider filing an issue about this. We will consider these requests on a case per case basis.

#### What if I find a bug in a supported platform?

If you are using the latest version of a chai project, and find a bug in a version we claim to support, then please raise a bug in the issue tracker for that project. It is likely that a patch-release will be made to fix this bug, where possible.

#### What does it mean to "stop supporting" a platform version? Will that version suddenly stop working?

When a new version of a platform is released, we will begin supporting it immediately - this means we will always accept and handle bug reports for any latest version of any supported platform. As soon as we can, we will add Continuous Integration tests for the latest released version of any platform. As older versions move to end-of-life, they will continue to be tested until the next _Major Version release_ of a specific project, and the support for the end-of-life version will be dropped in the next _Major Version release_ of our project.

For example, currently Chai@4 supports Node.js@4. All releases of Chai@4 will continue to support Node.js@4 even though this version is EOL. Chai@5 is not yet released at the time of writing (June 2019) and as such will not support any versions of Node.js before June 2019, including Node.js@4,5,6,7,9 and 11. When Chai@5 is released, it's support matrix will be fixed until Chai@6 is released.
