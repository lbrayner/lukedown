In `autoload/db.vim`:

```vimscript
    let lines = ['']
    echom a:cmd
    let job = jobstart(a:cmd, {
          \ 'env': env,
          \ 'on_stdout': function('s:nvim_job_callback', [lines]),
          \ 'on_stderr': function('s:nvim_job_callback', [lines]),
          \ 'on_exit': { id, status, _ -> a:on_finish(lines, status) },
          \ })
```

Then run (Command-line):

```vimscript
:call jobstart(<whatever was echoed>,{'on_stdout':{j,d,e->append(line('.'),d)}})
```
