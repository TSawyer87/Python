# FZF syntax

Let's go over syntax so we can search more efficiently. Fortunately for us, there aren't many to learn.

- `^` is a prefix exact match. To search for phrase starting with "welcome", we do `^welcome`.
    
- `$` is a suffix exact match. To search for phrase ending with "my friends", we do `friends$`.
    
- `'` is an exact match. To search for phrase "welcome my friends", we do `'welcome my friends`.
    
- `|` is an "or" match. To search for either "friends" or "foes", we can use `friends | foes`.
    
- `!` is an inverse match. To search for phrase containing "welcome" and not "friends", we can use `welcome !friends`
    

We can mix and match the above. For example, `^hello | ^welcome friends$` searches for phrase starting with either "welcome" or "hello" and ending with "friends".

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#finding-files)Finding files

To search for files inside Vim using FZF.vim plugin, we can use `:Files` method. Run `:Files` from Vim and you'll be prompted with FZF search prompt. Pretty cool!

[![Files](https://res.cloudinary.com/practicaldev/image/fetch/s--GRyK6ICL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/ek0jfaty699mm14cuvg3.gif)](https://res.cloudinary.com/practicaldev/image/fetch/s--GRyK6ICL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/ek0jfaty699mm14cuvg3.gif)

FZF.vim file finder is best used with a mapping. I've used `<Leader>f` and `Ctrl-p` in the past and I am currently mapping it to `Ctrl-f`.  

```
nnoremap <silent> <C-f> :Files<CR>
```

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#finding-in-files)Finding in files

To search inside files, we can use FZF.vim's `:Rg` command. Alternatively, we can use `:Ag` ([The Silver Searcher](https://github.com/ggreer/the_silver_searcher)). For this article, I will use `:Rg`.

[![Rg](https://res.cloudinary.com/practicaldev/image/fetch/s--2GfOi2wU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/f1bg4f308201ezvc8xzg.gif)](https://res.cloudinary.com/practicaldev/image/fetch/s--2GfOi2wU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/f1bg4f308201ezvc8xzg.gif)

Mine is mapped to `<Leader>f`.  

```
nnoremap <silent> <Leader>f :Rg<CR>
```

Side note: FZF.vim `:Rg` option also searches for file name in addition to the phrase. If you think this is an issue, check out this [comment](https://github.com/junegunn/fzf.vim/issues/346#issuecomment-288483704). I added this in my `.vimrc`:  

```
command! -bang -nargs=* Rg call fzf#vim#grep("rg --column --line-number --no-heading --color=always --smart-case ".shellescape(<q-args>), 1, {'options': '--delimiter : --nth 4..'}, <bang>0)
```

With the above, every time we invoke `Rg`, FZF + ripgrep will not consider filename as a match in Vim.

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#other-searches)Other searches

FZF.vim provides many other search commands. You can check them out [here](https://github.com/junegunn/fzf.vim#commands).

Here's what my FZF mappings look like:  

```
" PLUGIN: FZF
nnoremap <silent> <Leader>b :Buffers<CR>
nnoremap <silent> <C-f> :Files<CR>
nnoremap <silent> <Leader>f :Rg<CR>
nnoremap <silent> <Leader>/ :BLines<CR>
nnoremap <silent> <Leader>' :Marks<CR>
nnoremap <silent> <Leader>g :Commits<CR>
nnoremap <silent> <Leader>H :Helptags<CR>
nnoremap <silent> <Leader>hh :History<CR>
nnoremap <silent> <Leader>h: :History:<CR>
nnoremap <silent> <Leader>h/ :History/<CR> 
```

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#replacing-grep-with-raw-rg-endraw-)Replacing grep with `rg`

Internally, Vim has two ways to search _in files_: `:vimgrep` and `:grep`. `:vimgrep` uses vim's built-in grep and `:grep` uses external tool which you can reassign using `'grepprg'`.

For example, if we want to search for "iggy" with `:grep`, we can run `:grep "iggy" . -R` (you may notice that Vim's `:grep` syntax is similar to terminal `grep` command; this is because `:grep` by default runs `grep -n $* /dev/null` on unix-based machine). The command above will search for string `"iggy"` recursively (`-R`) from current location (`.`).

Vim allows us to change the program used by `:grep`. We can tell Vim to use ripgrep instead of grep by adding this inside our vimrc:  

```
set grepprg=rg\ --vimgrep\ --smart-case\ --follow
```

Now when we run `:grep` inside Vim, it will run `rg --vimgrep --smart-case --follow` instead. For more information what the options above mean, check out `man rg`. I can now run a more succinct command `:grep "iggy"` instead of `:grep "iggy" . -R`.

Vim `:grep` command uses quickfix to display results. I won't go over quickfix here because it's outside this article's scope. We can use `:copen` to display quickfix window and `:cclose` to close quickfix window. Try it!

You might wonder, "Well, this is nice but I never used `:grep` in Vim, plus can't we just use `:Rg` to find string in files? When will I ever need to use `:grep`?"

That is a very good question. The answer to "why do we need grep in Vim?" is that it will let us to do what I'll going to cover next: search and replace in multiple files.

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#search-and-replace-in-multiple-files)Search and replace in multiple files

Modern text editors like VSCode makes it very easy to search and replace string across multiple files. If I may confess, in the beginning when I had to search/replace string in multiple files, I used VSCode because doing it in Vim, although possible, takes too long... _until now_.

I will show you two different tricks to _easily_ do search and replace phrases across multiple files in Vim.

**The first method** is to replace _ALL_ matching phrases in our project. We will need to use `:grep`. Let's say you want to replace all instance of "pizza" with "donut". Here's what you do:  

```
:grep "pizza"
:cfdo %s/pizza/donut/g | update
```

That's it? Yup! That's it. Let me break down the steps:

1. `:grep pizza` uses ripgrep to succinctly search for all instances of "pizza". By the way, this would still work even if we didn't reassign ripgrep to replace default grep. We would have to do `:grep "pizza" . -R` instead of `:grep "pizza"`.
2. We run `:cfdo` because `:grep` uses quickfix.`:cfdo` executes any command we pass (in this case, our command is `%s/pizza/donut/g`) on all entries in our quickfix list. To run multiple commands, we can chain it with pipe (`|`). The first command we are executing is pizza-donut substitution: `%s/pizza/donut/g`. The second command, `update`, saves each file after the first is finished.

Let's discuss the second way.

**The second method** is to search and replace in select multiple files instead of all files using buffers. Here we can choose which files we want to perform select and replace.

1. Clear our buffers (`:Buffers`) first. Our buffers list should contain only the needed files. We can clear it with `%bd | e# | bd#` (or restart Vim).
2. Run `:Files`.
3. Select all files you want to perform search and replace on. To select multiple files, use `Tab` / `Shift+Tab`. This is only possible if we have `-m` in `FZF_DEFAULT_OPTS`.
4. Run `:bufdo %s/pizza/donut/g | update`.

Our command `:bufdo %s/pizza/donut/g | update` looks similar to `:cfdo %s/pizza/donut/g | update`. That's because they are. Instead of performing substitution on all _quickfix_ (`cfdo`) entries, we perform our substitution on all _buffer_ (`bufdo`) entries.

# [](https://dev.to/iggredible/how-to-search-faster-in-vim-with-fzf-vim-36ko#conclusion)