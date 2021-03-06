Title: Internalizing Packages (Creating Recompiled Packages)
Published: 20160427
Author: Rob Reynolds
Tags: HowTo, Packaging, Internalize
Keywords: howto, chocolatey, packages, internalize
Summary: The community repository has quite a few packages out there that have great logic. Learn how to take advantage of them without the hit to the internet! 
---
**Note:** Originally posted on [Puppet's blog](https://puppet.com/blog/chocolatey-creating-recompiled-packages). *Reposted with permission.*

Sometimes creating packages from scratch can be an involved process. Not all software installers are created equal (and not all are easily automated either)! Thankfully there is already a tremendous resource you can use to make the process of getting your software all packaged up even smoother.

On [chocolatey.org](https://chocolatey.org/packages), you will find packages with all of the install logic you need to automatically install your software. However, many of these publicly available packages also rely on software that is available from official distribution points because they are subject to [software licensing and copyright law](https://en.wikipedia.org/wiki/Software_license). Unless you’re granted the right to distribute the software via the license, you can’t redistribute it publicly. These laws do not apply when you use internal packages, and that is a good thing!

Why? Downloading software from the internet creates a failure point because it may not be available, the software vendor site could go down, etc. With internal packages, you don’t have to worry about any of that. You can create internal packages and embed the software directly in the package and/or use internal file shares.

This is where recompiling packages comes in. Recompiling a package lets you take an existing package and internalize all of the resources to embedded/internal resources so you can reuse the install logic without the hassle of downloading stuff from the internet. This guarantees complete control, trust, reliability, and repeatability of a package for organizations that have a low tolerance for production issues.

Creating your own recompiled packages is easy. In fact, we already have [documentation](https://docs.puppet.com/pe/latest/windows_modules.html#copy-an-existing-package-and-make-it-internal-repackaging-packages) that walks you through the process step by step!

Recompiling a Chocolatey package at a high level involves:

1. Downloading and unpacking the existing package as a zip file.
2. Downloading the resources the package has and putting them in the package.
3. Editing the install script to point to the internal software.
4. Packaging it back up.
5. Pushing it to your internal server.

And that’s it!

Recompiling is a great way to quickly get your organization up to speed on managing software with Chocolatey packages . When you are ready, we have [documentation](https://chocolatey.org/docs/how-to-recompile-packages) that takes you through all of the necessary steps. We also have [Package Internalizer](https://chocolatey.org/docs/features-automatically-recompile-packages) which will do this for you automatically.