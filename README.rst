===================================================
 SCaLE 14x abstracts (submitted) and slides (later)
===================================================

Open Source ARM Linux Kernels and Graphics Driver Status Update: Have Things Progressed Since Last Year?  (yes, but...)
=======================================================================================================================

Abstract
--------

In the past year, although not all "platforms" have enjoyed the same level of activity,
the mainline kernel and several ARM graphics stacks have made significant progress in
the open source world.  In addition to several vendors pushing more of their device
trees into the mainline patch queue, as well as incorporating the ARM DRM headers,
there are several active projects on the graphics side, including Xorg armsoc,
RaspberryPi VC4 and DRM drivers, Tegra/Nouveau (whole stack), and etna_viv (Vivante)
for Freescale iMX6 (older iMX2x hardware is "fully mainlined).  Current state of
software, documentation, and usability is discussed (kernel/drivers and application
issues, etc).

Currently active platforms:

* RaspberryPi/Broadcom VideoCore4 driver and card definition in mesa/rpi-kernel (vc4)
* Tegra Nouveau/Mesa and kernel patches (in progress upstream: https://github.com/NVIDIA/tegra-nouveau-rootfs)
* Exynos (Mali) xf86-video-armsoc driver in Xorg, as yet unreleased (tested on Samsung Chromebook)
  - xf86-video-mali and limadriver projects stale and based on vendor architecture

* iMX (Vivante) etna_viv driver, libdrm, mesa forks (still in flux)
  - some recent work, some not-so-recent (several forks on github)

* Freedreno (Adreno) new mainline interface, still active (but we have no hardware for testing)

Current but (mostly) inactive platforms

* Tegra20/30 core drm mainlined, xf86-video-opentegra works (performance "okay") but minimal mesa support
* TI Beagle/PowerVR has basic mainline 4.x kernel support
  - 3D is still SGX-based (but working), xorg 2D drivers are mostly edgey and/or stale (use fbturbo or fbdev)

The majority of the above work takes place in either github or FreeDesktop/Xorg repos
(others are largely stale forks).

.. Note:: Much of the above is available in the Gentoo/ARM overlay kernel-sources
   and graphics packages (eg, nouveau-sources has tested patches incorporated)
   as well as Robert C Nelson's `LinuxOnArm wiki`_.

.. _LinuxOnArm wiki: https://eewiki.net/display/linuxonarm/Home

Autotools The Easy Way (no, I'm not kidding...)
===============================================



Open Document Formats and reStructuredText (less pain, more geek)
=================================================================



Open Source CyberSecurity: Your Tax Dollars At Work
===================================================


'A' is for Appliance, 'B' is for Buildroot
==========================================

What's that, you're *not* currently in the market for a new way to build OS images for your toaster?
That's fine, go ahead and keep your NetBSD on your trusty-old-scorcher-of-bread\ :superscript:`1` -- kitchen appliances
are not exactly the flavor of appliance under discussion. Instead we'll be talking about using
Buildroot to turn common dev boards (Raspberry Pi, Beaglebone Black, MinnowBoard Max, etc) into 
embedded Linux "appliances" with a narrow purpose in life.

:superscript:`1` https://www.embeddedarm.com/software/arm-netbsd-toaster.php

The Secret Life of U-Boot
=========================

Please put on your submarine-commander hat, because it's time to explore some of the
depths of U-Boot. You don't really believe U-Boot is just an innocent little bootloader 
that only knows how to start the kernel on your embedded device in exactly the same
manner day after day, do you? Certainly not! 

* U-boot transports valuable images (for merely a small fee) when the local network hardware is on strike
* U-boot has been spotted doing Jenkins' dirty work of "reprogramming" boards that need to be taught a lesson
* U-Boot has even been known to conspire with JTAG debuggers to do bare NAND programming without a permit
