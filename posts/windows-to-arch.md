---
title: "Goodbye Windows, Hello Arch"
date: "2026-03-22"
---

# Why I Switched from Windows to Arch Linux as a Developer

*March 22, 2026*

---

I never planned to switch. Windows was fine. WSL was running, VS Code was open, Git was working. Everything was "fine." But fine is a dangerous word — it's what you say right before you start noticing all the things that quietly annoy you.

This is about why I made the jump to Arch Linux, what actually happened when I did, and whether it was worth it.

---

## It started with WSL

For a while, WSL felt like a smart middle ground. Linux tools, Windows comfort. But the more seriously I got into development, the more I felt the seams. File system performance was noticeably slower across the boundary. Running anything GPU-related was a mess. And there was always this nagging feeling that I was working *around* my OS instead of *with* it.

I wasn't solving problems anymore. I was patching workarounds with more workarounds.

---

## Why Arch specifically

Honestly? Curiosity and stubbornness.

I didn't want Ubuntu or Mint — distros that hold your hand a little too much. I wanted to actually understand what's running on my machine. Arch forces you to build your system piece by piece, which means when something breaks (and it will), you know exactly where to look.

Also, the AUR. Having access to almost any package without jumping through hoops is one of the best things about Arch. And the rolling release model means you're always on the latest — no waiting for the next LTS to get a recent version of something.

---

## The setup was brutal, and I mean that as a compliment

Setting up Arch on a machine with an NVIDIA GPU and an Intel iGPU is not a relaxing afternoon. There were display issues. There were boot issues. I spent more time than I'd like to admit just getting my external monitor to show up correctly.

But every problem I solved taught me something real. I learned how display managers work. I learned how kernel modules load. I learned the difference between Wayland and X11 in a way no tutorial ever made clear to me.

That kind of learning doesn't happen when your OS just works out of the box.

---

## What actually got better

**The terminal feels native.** Not bridged, not emulated — just there. Everything snappy.

**Package management is a joy.** `pacman` is fast. The AUR fills every gap. I spend way less time hunting for `.exe` installers or wondering why something doesn't have a Windows build.

**My machine feels like mine.** I run GNOME on Wayland, my terminal has a dark neon theme, my editor looks exactly how I want it. Nothing I didn't put there is running in the background.

**Dev tools just work.** Node, Python, Go — install from the terminal, no weird PATH issues, no permission errors, no "run as administrator."

---

## What's still annoying

NVIDIA on Linux is still a pain point. Getting DRM and Wayland to cooperate took real effort. Widevine for Chrome needed manual setup. Some apps have tray icon quirks on Wayland that I'm still living with.

And yes, sometimes a system update breaks something. That's the trade-off with rolling release — you get the latest, but you also get to debug the latest.

---

## Was it worth it?

Yeah. Genuinely.

Not because Arch is objectively better than Windows for every use case. But for development work, especially when you care about actually understanding your environment, it's a completely different experience.

I feel more in control of my machine now. When something breaks, I fix it. When I want something to work differently, I change it. That's a mindset shift as much as it is an OS switch.

If you're thinking about making the jump — do it. Just don't do it the week before exams.
