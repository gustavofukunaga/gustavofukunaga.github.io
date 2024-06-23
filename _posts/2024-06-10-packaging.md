### Packing Perl Software in Debian: A Personal Experience

### Introduction

Embarking on the journey of packaging Perl software for Debian, I realized the importance of this task for the community. Though it seems daunting, with patience and attention to detail, one can make a significant contribution. Here, I will share my experience following two tutorials and my attempt with the Devel::AssertOS library.

### Tutorial 1: Setting Up the Development Environment

The first step was to set up the development environment, which consisted of:
1. Configuring the Debian system with all necessary tools.
2. Installing essential packages such as `devscripts`, `debhelper`, `dh-make-perl`, among others.
3. Setting up `dpt` (Debian Perl Team) to facilitate packaging and package submission.

### Tutorial 2: Packaging Perl Libraries

I followed the [Debian Packaging Tutorial - Part 2](https://joenio.me/blog/2024/05/15/tutorial-de-empacotamento-debian-parte-2/) by Joenio Marques da Costa, which describes how to create packages for Perl libraries and submit them to the official repositories via the Debian Perl Group.

#### Tutorial Outline

1. **Selecting a Candidate Package**: I chose the `Devel::AssertOS` library from the suggested options.
2. **Creating the Package**: I used `dh-make-perl` to generate the initial package template.
3. **Fixing the Initial Template**: I adjusted the `debian/copyright` file to include the correct year and author information. I also reviewed and updated the `debian/control` file as necessary.
4. **Building the Package and Checking for Issues**: I used `pbuilder` to build the package in an isolated environment and ran `lintian` to check for compliance.
5. **Running Automated Tests**: I used `autopkgtest` to ensure the package passed functional tests.
6. **Submitting the Package**: I prepared the package for submission to the Debian Perl Group repository.

#### Challenges Faced

During the final step, while trying to build the `Devel::AssertOS` package, I encountered dependency issues such as version conflicts and some dependencies missing. These problems prevented the completion of the packaging process but provided valuable insight into the real challenges faced during this process.

### Conclusion

Packaging software for Debian requires meticulous attention to detail and patience. Although I couldn't finish packaging the `Devel::AssertOS` library due to dependency issues, the experience was enriching. I encourage everyone interested in contributing to the Debian community to try following these tutorials and face the challenges head-on. Even without completing the process, the learning experience is invaluable.
