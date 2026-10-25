---
name: thh-source-check
description: Checks each factual claim in a draft (a family handout, FAQ, blog post, or navigator note) against official sources, and rewrites or flags any claim the sources don't support. Use before a Texas Health Help document is published or sent to a family.
license: Apache-2.0. Adapted from the corrective RAG workflow in https://github.com/Shubhamsaboo/awesome-llm-apps (rag_tutorials/corrective_rag). See THIRD_PARTY_NOTICES.md.
---

# Texas Health Help source check

Review a draft so that every factual claim is supported by a source the navigator can verify. This skill corrects drafts. It does not write new policy.

## Steps

1. **Extract the claims.** List each factual statement in the draft: program names, eligibility rules, amounts, dates, phone numbers, addresses, and deadlines. Skip opinions and general encouragement.
2. **Retrieve sources.** For each claim, search the official Texas Health Help guides with `mcp__Texas_Health_Help__search_guides` and `mcp__Texas_Health_Help__search_blog_posts`. Use `get_blog_post` or `get_contact_info` when a claim points to a specific page or contact.
3. **Grade each source.** Mark each claim as one of:
   - **Supported:** a retrieved source states it. Record the source URL and the exact wording.
   - **Partly supported:** the source is related but differs in a detail such as a date, amount, or condition.
   - **Unsupported:** no retrieved source states it.
4. **Correct once.** For partly supported or unsupported claims, search again with a different query, such as a program's official name or an alternate spelling. Do this one time only.
5. **Report.** For each claim, show the original text, its grade, the source URL, and the corrected wording if one is needed.

## Output

- **Supported:** claims that can go out as written, with source links.
- **Corrected:** the original and the corrected wording, with the source for the correction.
- **Remove or verify:** unsupported claims. Recommend removing them, or sending them to the navigator to confirm with the program.
- **Before publishing:** "Eligibility, amounts, and deadlines change. A navigator should confirm the final text."

## Limits

- Do not rewrite a claim so it sounds more certain than the source does.
- If a claim is not in the official sources, do not approve it, even if it sounds correct.
