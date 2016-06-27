
svn log:

```
alias slog="svn log -v --limit 4"
alias svn log="svn log -l 4 | perl -l40pe 's/^-+/\n/' | less" 
```
