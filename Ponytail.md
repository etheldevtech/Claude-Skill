Install Ponytail in Ubuntu

1. Install node
```
sudo apt update
sudo apt install -y nodejs npm
```
OR
```
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs

node --version
```


2. Install Ponytail in Claude Code
```
claude --version
claude plugin marketplace add DietrichGebert/ponytail
claude plugin install ponytail@ponytail
```

3. Uninstall
```
claude plugin uninstall ponytail@ponytail
```

4 How to use 
| Command | What it does | Sample |
| --- | --- | --- |
| /ponytail | Show current level (or turn it on if off) | /ponytail |
| /ponytail lite | Mild mode — do the task, mention simpler options | /ponytail lite |
| /ponytail full | Default mode — smallest working code + short risks | /ponytail full |
| /ponytail ultra | Strict mode — questions the request first | /ponytail ultra |
| /ponytail off | Turn Ponytail off for this session | /ponytail off |
| /ponytail-help | Show the help card | /ponytail-help |
| /ponytail-review | Review current changes (bugs, security, what to cut) | /ponytail-review |
| /ponytail-audit | Audit the whole repo (most important first) | /ponytail-audit |
| /ponytail-debt | Collect deferred shortcuts into a list | /ponytail-debt |
| /ponytail-gain | Show impact scoreboard (less code / cost / time) | /ponytail-gain |
| /ponytail band | Hide / show the cost band above the prompt | /ponytail band |

```
/ponytail-review
/ponytail full
```
