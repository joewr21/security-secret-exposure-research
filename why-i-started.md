<!-- 연구 레포 security-secret-exposure-research/why-i-started.md — 원래 프로필에 있던 긴 서사(숫자만 교정). README의 '왜 시작했나'에서 링크. -->

# Why I started

My interest in security started with a mistake of my own.

While coding, I once pushed a key to a public place by accident. Some friends of mine had made similar mistakes.

That's when this thought hit me:

> "If I'm doing this, aren't other people making the same mistake?"

So I started looking for myself.

I combined several open-source tools into a system that automatically analyzes publicly distributed apps and sites. It downloads a package, takes it apart on my own computer, and looks for credentials or config files that got included by accident.

The first time I ran it, real keys came out — far too many of them.

At first I thought I'd built something wrong; it was sometimes flagging dummy or test values as real. I went through them, fixed how the structural checks worked, and realized there genuinely were cases where live credentials had been shipped as-is. That's when it became more than curiosity.

## What I found

So far I've scanned **91,287 publicly distributed apps and sites** — 41,127 mobile apps and 50,160 web endpoints — and found **8,417 exposures**.

These numbers do **not** mean "X% of all apps are vulnerable." What I analyzed isn't a random sample meant to represent the whole market — it's simply a tally of the exposures I happened to find while looking.

Among them were apps from large companies, and apps used by children. What surprised me most: **141 apps shipped a cloud service-account credential inside the distributed package** — a credential that, depending on its permissions, can authenticate to real backend resources. That should never sit in a file anyone who downloads the app can pull out.

## The line I hold

My analysis happens **offline only**. I take publicly distributed packages and analyze them on my own computer.

- I don't attack live servers, don't intercept anyone's traffic, and don't use the keys I find to log in or open up data.
- Even to check whether a key is genuine, I only go as far as **structural verification that's possible locally** — never authenticating against a real service.
- When something looks serious, I don't publish it — I **report** it. Usually: the developer directly → if no reply, **KrCERT/KISA** → the platform provider when needed.
- I never reveal which company it was, which app, or what the key was.

## Why I keep doing it

I didn't start this to make money — I was just curious. Finding a mistake hidden inside a file and being able to tell someone before it gets abused is genuinely satisfying: someone avoids a bill they never saw coming, or someone's personal data stays out of harm's way. People make mistakes — I did, and so did my friends — and I find real joy in helping quietly fix them.

---

← Back to the [summary & charts](./README.md) · Contact: security@leejooho.me
