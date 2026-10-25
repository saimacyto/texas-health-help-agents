---
name: thh-document-qa
description: Answers navigator questions using only the documents provided (program guides, intake forms, county lists, policy PDFs or text files), with a citation for every claim. Use when a navigator asks a question about a specific document or folder of documents.
license: Apache-2.0. Adapted from the RAG patterns in https://github.com/Shubhamsaboo/awesome-llm-apps (rag_tutorials/hybrid_search_rag and rag_tutorials/local_rag_agent). See THIRD_PARTY_NOTICES.md.
---

# Texas Health Help document Q&A

Answer questions from the documents the navigator names. The documents are the only source for the answer.

## Steps

1. **Find the documents.** Use `Glob` to list the files the navigator named, or the folder they pointed to. If none were named, ask which documents to use. Do not search the whole machine.
2. **Find relevant passages.** Use `Grep` with several phrasings of the key terms, including synonyms (for example "Medicaid", "Texas Medicaid", "STAR"). Use `Read` with offsets to read the matching sections in full. Reading a whole document is rarely needed.
3. **Grade each passage.** For each one, decide whether it directly answers the question. Keep only the passages that do.
4. **Answer only from the kept passages.** Write the answer in plain language, at a reading level a family can follow.
5. **Cite every claim.** Give the file name and the section heading or page number, for example `[guide.pdf, p. 4]`.
6. **If the documents don't answer it,** say "The provided documents don't cover this" and name what is missing. Do not fill the gap from general knowledge.

## Output

- **Answer:** plain-language answer with citations inline.
- **Sources used:** file and section list.
- **Not covered:** anything the question asked that the documents don't answer.
- **Note:** "Rules and amounts change. Confirm with a Texas Health Help navigator before the family acts on this."

## Limits

- Never state an eligibility decision, income limit, or deadline unless the cited passage contains it.
- Clinical questions are out of scope. Say a clinician should answer them.
