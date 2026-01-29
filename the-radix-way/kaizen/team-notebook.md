---
description: Informal but searchable notes. Nothing too minor to share
---

# Team Notebook

{% hint style="success" %}
A single page in reverse chronological order of notes and findings

Use it to openly share notes for (semi-)posterity with the rest of the team

Simply add a new row, record the date, your name and a brief note.
{% endhint %}

<table data-full-width="false"><thead><tr><th width="122.39453125" valign="top"></th><th width="126.28515625" data-type="users"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">2026-01-20</td><td><a href="https://app.gitbook.com/u/cDtSDG3YYaStO3Q7KaOgwuzaKx53">Steve Harris</a></td><td valign="top"><p>Use GitBook’s Azure (Microsoft Entra ID) integration for the simplest, usually free, authenticated access: create an Entra app, add GitBook’s redirect URI, then restrict viewers by setting the Enterprise app to Assignment required and assigning only a group/user list. For page-level gating, split into public and private spaces.</p><p>See</p><ul><li><a href="https://docs.gitbook.com/publishing-documentation/visitor-authentication/setting-up-azure-ad">https://docs.gitbook.com/publishing-documentation/visitor-authentication/setting-up-azure-ad</a></li><li><a href="https://gitbook.com/docs/publishing-documentation/authenticated-access/setting-up-oidc">https://gitbook.com/docs/publishing-documentation/authenticated-access/setting-up-oidc</a></li></ul></td></tr><tr><td valign="top">2026-01-29</td><td><a href="https://app.gitbook.com/u/cDtSDG3YYaStO3Q7KaOgwuzaKx53">Steve Harris</a></td><td valign="top">Gitbook does not appear to integrate with Zotero <span data-gb-custom-inline data-tag="emoji" data-code="1f612">😒</span>. <br>But it does allow inline citations either double clicking on the selected text and choosing the appropriate icon, via the keyboard <code>command+option+f</code>, or by typing <code>/</code> at anytime.<br>You can then paste in the citation or URL or reference that you wish.<br>If you are using Zotero then I've made a Zotero reference style in the 'author+date+doi' format. You need to <a href="https://www.zotero.org/support/styles">import</a> this into your Zotero styles. You can download it <a href="https://gist.github.com/docsteveharris/8fac8680ba9752ee9dd440f41fecd5d7">here</a>. Then use the 'Copy Citation' menu or shortcut <code>(command+shift+A)</code> on my mac and you should get something that looks like <code>(Gohil </code><em><code>et al.</code></em><code>, 2024,</code> <a href="https://doi.org/10.1001/jama.2024.6248"><code>https://doi.org/10.1001/jama.2024.6248</code></a><code>)</code> that you can paste directly at the end of the sentence or as inline annotation (as you wish).<br><br>Here's an example with an inline annotation using a long form, and an 'author-date' reference directly in the text.<br><br>The <a data-footnote-ref href="#user-content-fn-1">INSPIRE cluster randomised trial</a> demonstrated that computerised provider order entry (CPOE) prompts reduced use of extended spectrum antibiotics.(Gohil <em>et al.</em>, 2024, <a href="https://doi.org/10.1001/jama.2024.6248">https://doi.org/10.1001/jama.2024.6248</a>)</td></tr><tr><td valign="top"></td><td></td><td valign="top"></td></tr></tbody></table>



[^1]: Gohil, S.K. _et al._ (2024) ‘Stewardship prompts to improve antibiotic selection for pneumonia: The INSPIRE randomized clinical trial’, _JAMA_ \[Preprint]. Available at: [https://doi.org/10.1001/jama.2024.6248](https://doi.org/10.1001/jama.2024.6248).
