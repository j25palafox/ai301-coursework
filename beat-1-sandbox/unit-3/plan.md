I reproduced issue #56: `StructuralChunker` returns 0 chunks for a non-empty document with no headings.

My plan is to update `_extract_sections()` so headingless content is retained as a neutral section with no heading hierarchy (`path=[]`, `level=0`) instead of being discarded. The existing `chunk()` flow can then handle that section normally, including the current semantic subchunking behavior for larger sections.

I’ll also update `test_document_with_no_headings` by removing the strict `xfail` and keeping its expectation that a non-empty headingless document produces at least one `Chunk`.

For verification, I’ll:
- rerun the reproduction that currently returns 0 chunks and confirm it produces at least one chunk;
- run `test_document_with_no_headings`; and
- run the full structural chunker unit test file to check that empty input, headed and nested documents, metadata, and large-section behavior still work as expected.

I’m keeping the scope limited to `ingestion/chunking/structural_chunker.py` and `tests/unit/test_structural_chunker.py`. I’m not planning to redesign heading detection or hierarchy handling, change token-limit or semantic chunking behavior, modify other chunkers, or do unrelated cleanup.

## Deviations

[What changed between the plan you posted and the change you built, and
why. If nothing changed, say so in your own words - "nothing changed;
the plan held" earns these points in full. Leaving this blank does not.]

No deviations from the planned implementation. The changes allow heading-less documents to retain their content and emit a level-0 section without modifying Markdown heading detection or hierarchy logic. The existing issue #56 regression test now passes without the `xfail` marker, and all 15 structural chunker unit tests pass.