---
title: "Who did it? Attributing state-backed hackers in the Middle East with open sources"
date: 2026-11-18
draft: true
description: "How analysts attribute state-linked APTs in the Middle East using only open sources, and why identities are the target defenders must protect first."
categories: ["Cybersecurity", "Geopolitics"]
tags: ["attribution", "OSINT", "APT", "Middle East", "IAM", "MITRE ATT&CK"]
---

> **Scope:** analytical overview based only on public sources (vendor, CERT and government reports, academic work, MITRE ATT&CK). No operational details, no indicators, no tooling.

## In one sentence

Attributing a cyber operation to a state is a probabilistic judgement, not a proof, and the most reliable thing defenders can do is protect the identities that these groups keep going after.

## Why it matters

When a hospital, ministry or energy company is breached, "who was behind it?" quickly becomes a political question: sanctions, diplomatic responses, even deterrence signalling. The Middle East is a dense theatre for this: regional rivalries, proxy dynamics and sophisticated state-linked groups all overlap. A wrong or overconfident attribution can escalate a crisis, while ignoring attribution altogether leaves defenders blind to who is likely to come next. As someone who studies strategic studies and works in IAM, I find the intersection fascinating: attribution is the *strategic* question, identity protection is the *practical* answer.

## Key points

1. Attribution is hard by design: false flags, shared tooling, contractors and proxies blur the picture.
2. OSINT attribution works by *clustering* evidence (infrastructure, malware, behaviour, targeting) and stating a **confidence level**, never certainty.
3. TTPs mapped to MITRE ATT&CK are more durable than technical artefacts, which are cheap to change.
4. Public reporting links several regional groups to Iranian state interests; names differ across vendors, so overlaps need care.
5. Across these campaigns, credentials and accounts are a recurring target, so phishing-resistant MFA, privileged access management and identity monitoring pay off whoever the attacker is.

## Why attribution is difficult

Rid and Buchanan's classic paper frames attribution as [an art as much as a science](https://doi.org/10.1080/01402390.2015.1115975): technical, operational and strategic layers each give partial answers, and the final call is a judgement under uncertainty. Several things make it harder still:

- **False flags.** Attackers can deliberately plant misleading clues. The best-known public case is the 2018 Winter Olympics "Olympic Destroyer" incident, where researchers described code artefacts that imitated another group's [Kaspersky analysis](https://securelist.com/olympic-destroyer-is-here-to-trick-the-industry/84295/). It was not in the Middle East, but the lesson transfers.
- **Proxies and contractors.** Governments may work through front companies or loosely affiliated operators, which makes "the state" versus "a criminal group" a spectrum.
- **Overlapping clusters.** Different vendors track the same activity under different names, and one name can bundle several teams.
- **Shared infrastructure and tools.** Commodity and publicly available tools mean that "same tool" does not mean "same actor".

## How OSINT attribution actually works (at a high level)

Open-source analysts, whether at vendors, CERTs or universities, tend to follow a similar logic, often inspired by the [Diamond Model](https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf): look at the *adversary*, *capability*, *infrastructure* and *victim*, and see which pieces hang together.

- **Public reporting as raw material.** Joint government advisories and vendor write-ups are the backbone. Comparing independent reports is the single most useful move: if unrelated teams reach the same conclusion, confidence rises.
- **Victimology.** Who is targeted (sectors, countries, timing relative to political events) says a lot about the likely sponsor's interests.
- **Behaviour over artefacts.** Domains and file hashes expire quickly. Behaviours (how access is gained, how persistence is kept) are stickier, and [MITRE ATT&CK](https://attack.mitre.org/groups/) catalogues them per group.
- **Stating confidence.** Good reports separate fact from assessment and say "low / moderate / high confidence". As a reader, always check which one you are looking at.

## Some publicly reported groups in the region

The following are only examples, using ATT&CK's public group pages. Vendor naming differs, and ATT&CK itself notes overlaps, so treat this as a map, not a verdict.

- [MuddyWater](https://attack.mitre.org/groups/G0069/): described in public reporting as a cyber-espionage group; a [US–UK–Australia–Canada joint advisory (CISA AA22-055A)](https://www.cisa.gov/news-events/cybersecurity-advisories/aa22-055a) assessed it as a subordinate element of Iran's Ministry of Intelligence and Security (MOIS). The advisory is government-sourced and explicit about the attribution. *(link not machine-checked: site blocks automated access)*
- [OilRig](https://attack.mitre.org/groups/G0049/): an Iran-linked group reported to target governments and sectors across the Middle East. Attribution here rests on vendor assessments rather than an official statement [unverified: confirm the strength of government attribution].
- [APT33](https://attack.mitre.org/groups/G0064/) and [Magic Hound](https://attack.mitre.org/groups/G0059/): other Iran-linked clusters in public reporting, with different mixes of aviation/energy targeting and social-engineering-heavy intrusions.

Notice the pattern: names, sponsors and confidence differ by source. That is exactly why analysts cross-check.

## Why identities are the recurring target

Looking at ATT&CK entries for these groups, a common thread is initial access via [phishing](https://attack.mitre.org/techniques/T1566/) and credential abuse, including [password spraying](https://attack.mitre.org/techniques/T1110/003/). That makes sense: a valid account is quiet, cheap and often more powerful than malware. Privileged and service accounts are especially valuable because they open the door to everything else.

## What IAM can do (and why it's attacker-agnostic)

The nice thing about identity defence is that it doesn't depend on getting attribution right:

- **Phishing-resistant MFA.** SMS codes and push approvals can be phished or fatigued; FIDO2/WebAuthn and passkeys bind authentication to the legitimate site. CISA publishes a [fact sheet on implementing phishing-resistant MFA](https://www.cisa.gov/resources-tools/resources/implementing-phishing-resistant-mfa) *(not machine-checked)*.
- **Privileged access management (PAM).** Fewer standing admin rights, just-in-time elevation, vaulted credentials and session recording shrink what a stolen password can do.
- **Monitoring identity signals.** Impossible travel, unusual consent grants, new MFA enrolments and spraying patterns are detectable if logs are collected and someone looks at them.
- **Zero Trust mindset.** Assume credentials will be stolen, so verify continuously and limit blast radius.

## What I'd do next

- Read two or three independent public reports on the same group and compare their confidence statements.
- Map a few of the ATT&CK techniques above to your own identity controls and note the gaps.
- For further study: compare how governments (joint advisories) and vendors word attribution, and what that implies for policy responses.

*Caveat: everything here is drawn from public sources and is an analytical simplification, not an assessment of any specific incident or organisation.*
