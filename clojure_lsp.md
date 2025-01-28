- High chance of there being errors if `deps.edn` attaches - `fidget` LSP
  progress message gets stuck ("Fetching libs for completion"), `:Fidget clear`
  clears it.
- When new dependency is declared, only solution is to close the Neovim session
  and re-open it, then start the server.
- Auto-completion stopped working this one time.
  - Was it 'omnifunc'? Or 'completefunc'?
    - Yes, precisely!
- Why won't new buffers created with `:edit` attach to `clojure_lsp`?
 - Fixed!
- Code action "Clean namespace" is "Organize imports".
- DiagnosticChanged autocmd was not created this one time.
