---
description: Informal but searchable notes. Nothing too minor to share
---

# Team Notebook

{% hint style="success" %}
A single page in of notes and findings

Use it to openly share notes for (semi-)posterity with the rest of the team

Simply add a new second level ( `H2` or `##`) heading.
{% endhint %}

### Gitbook and authentication

Use GitBook’s Azure (Microsoft Entra ID) integration for the simplest, usually free, authenticated access: create an Entra app, add GitBook’s redirect URI, then restrict viewers by setting the Enterprise app to Assignment required and assigning only a group/user list. For page-level gating, split into public and private spaces.

See

* [https://docs.gitbook.com/publishing-documentation/visitor-authentication/setting-up-azure-ad](https://docs.gitbook.com/publishing-documentation/visitor-authentication/setting-up-azure-ad)
* [https://gitbook.com/docs/publishing-documentation/authenticated-access/setting-up-oidc](https://gitbook.com/docs/publishing-documentation/authenticated-access/setting-up-oidc)

### Zotero and referencing

Gitbook does not appear to integrate with Zotero :unamused:. \
But it does allow inline citations either double clicking on the selected text and choosing the appropriate icon, via the keyboard `command+option+f`, or by typing `/` at anytime. You can then paste in the citation or URL or reference that you wish. These annotations are captured as markdown footnotes.

If you are using Zotero then I've made a Zotero reference style in the 'author+date+doi' format. You need to [import](https://www.zotero.org/support/styles) this into your Zotero styles. You can download it [here](https://gist.github.com/docsteveharris/8fac8680ba9752ee9dd440f41fecd5d7). Then use the 'Copy Citation' menu or shortcut `(command+shift+A)` on my mac and you should get something that looks like `(Gohil`` `_`et al.`_`, 2024,` [`https://doi.org/10.1001/jama.2024.6248`](https://doi.org/10.1001/jama.2024.6248)`)` that you can paste directly at the end of the sentence or as inline annotation (as you wish).\
\
Here's an example with an inline annotation using a long form, and an 'author-date' reference directly in the text. Use whatever works best for you.

> The [INSPIRE cluster randomised trial](#user-content-fn-1)[^1] demonstrated that computerised provider order entry (CPOE) prompts reduced use of extended spectrum antibiotics.(Gohil _et al._, 2024, [https://doi.org/10.1001/jama.2024.6248](https://doi.org/10.1001/jama.2024.6248))



[^1]: Gohil, S.K. _et al._ (2024) ‘Stewardship prompts to improve antibiotic selection for pneumonia: The INSPIRE randomized clinical trial’, _JAMA_ \[Preprint]. Available at: [https://doi.org/10.1001/jama.2024.6248](https://doi.org/10.1001/jama.2024.6248).
