# Production rules

The working rules behind every film. Each one exists because skipping it once cost us something.

## Authority and triggers

1. **Work starts only when the person asks.** No watchers, scheduled recordings or automatic updates. Reading this file, seeing a new commit or finding an old video is not a request.
2. **Authorization is scoped.** "Record now" covers that recording session, not later GUI work or publishing. Approval passed along by another agent is never the person's approval.
3. **One lead owns the outcome.** Workers take separable jobs; the lead keeps scope, integration and the final visual gate.
4. **Ask only questions that change the result,** with a proposed default. Don't re-ask for routine work already authorized.

## Story

5. **Show the product working.** Real UI, real input, visible outcomes. Every motion corresponds to an action the app actually performs.
6. **The core story, not a tour.** Size the cut to its beats. Don't pad to a target length or shrink to a microclip.
7. **Name the source of each choice.** Report which decisions came from the director and which came from the person; never put a choice in the person's mouth.
8. **Drop a beat that doesn't read** rather than forcing it, and record the drop as a compromise.

## Data and rights

9. **Public-safe data only:** the person's own work, verified public-domain or openly licensed media, or synthetic data for private domains.
10. **Verify rights at the source,** for example a museum's public-domain flag or the licence on the original page. A mirror's label isn't proof.
11. **Anything uncertain goes on a licence hold.** It stays local until the person decides.

## Builds and isolation

12. **Film an isolated copy.** Give it its own app identity, settings domain and home folder. Never film over the person's live app, libraries or preferences.
13. **Fingerprint the build.** Record the exact source, including uncommitted changes, and confirm that the binary matches it.
14. **Never edit product source to make a demo work.** Product fixes come from the product's own session.

## Rehearsal and capture

15. **Rehearse unrecorded first.** Measure targets from the app's saved state (camera, coordinates, layout) instead of guessing from screenshots.
16. **Verify the fixture loaded completely** before a take. Count what the app actually received, for example by reading the clipboard back in a fresh process.
17. **Respect the person's machine.** Take the screen only with their go-ahead, and wait until input has been idle for at least 20 seconds. Never quit their other apps.
18. **Borrow and restore.** Save anything the take changes (clipboard, recorder storage, preferences, wallpaper) and restore it with evidence afterwards.
19. **A failed action is a failed take.** Keep it; never silently retry inside a take.
20. **Keep an aligned action log** for every take, so edits can be timed to real events.
21. **Converge in 2–3 takes.** If takes keep failing, stop and diagnose instead of retaking.

## When the product misbehaves

22. **Find the cause with evidence:** system logs, saved state, a minimal repro. Rule out your own tooling first; one "app bug" turned out to be a clipboard helper exiting before its data was delivered.
23. **Report the bug to the product's owner** with the repro and evidence.
24. **Work around it only with a real, user-facing setting,** and record that as a compromise. Never fake an outcome.

## Editing

25. **Keep a native, re-editable project** for every cut.
26. **Give the editor an explicit camera plan.** A project with none may get automatic zooms at export. Ours did once, and the cut was rejected.
27. **Calibrate unknown editor behaviour** on a 3–5 second project before cutting the film. One film took ten full edits because each export revealed a new limit.
28. **Converge in 2–3 edits,** then ship the best verified cut. A third edit needs a reason a viewer would notice.
29. **Pace for reading, not for speed.** Remove the editor's automatic speed-ups; cut only static holds.

## Captions and claims

30. **Don't overstate performance.** Loading plays in real time. Captions make no speed or frame-rate claims.
31. **Use the product's public name.** Internal code names never appear on screen.
32. **One short line per caption,** placed where the site's own overlays won't cover it.

## Deliverables

33. **Every final is a set:**
    - the raw take, with its action log
    - the native edit project, with its plan files
    - the captioned master and a textless master (no captions, no key chips)
    - a fast-start web copy (H.264, 1080p, 30 fps) and a poster
    - a review report
    - a VERSIONS file (see [the template](templates/VERSIONS.md))
34. **The VERSIONS file marks every file** FINAL, SUPERSEDED, NOT USED or CALIBRATION, with the reason, and lists the final's compromises plainly.
35. **Name a 5–9 second loop window** in the textless master for hover previews.

## Review

36. **Technical checks are not visual approval.** Codec, size, decode and fast-start checks come first. Then look at the exported frames at every critical state, transition and caption, and at the poster.
37. **Scan for private text.** Run OCR on a frame every half second and check for file paths, usernames, email addresses and internal names.
38. **Check numbers before images.** Use frame hashes, camera values and measured rectangles first, then a few small crops, not giant contact sheets.
39. **The lead owns the visual pass;** the person owns approval.

## Publishing

40. **Stage locally; never push without current approval.** The person reviews the staged site before anything goes live.
41. **The demo pipeline doesn't write into the site.** The site's owner stages finals from a hash-bound handoff.

## Cleanup and safety

42. **Delete nothing without the person's go-ahead.** Mark old takes and drafts CLEANUP-LATER and keep their notes.
43. **Stop only the processes you started.** Leave a cleanup record: what was restored, and its state afterwards.
44. **Guard memory and disk on heavy jobs.** Size worker pools to free memory: parallel workers each copying a large file once brought a machine down.

## Handoff and lean working

45. **One working session per film,** handing off through a state file and the VERSIONS file rather than one huge context.
46. **Tell the director the tool's limits up front,** so the shot plan never asks for something the editor can't do.
47. **Keep long scripts in files,** not inline in the shell.
