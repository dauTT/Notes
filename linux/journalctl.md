# journalctl

### What is Journalctl used for

{% embed url="https://www.mvorganizing.org/what-is-journalctl-used-for/" %}

### Retain last two day logs:

```text
journalctl --vacuum-time=2d
```

### FAQ

#### journal does not print all the logs \(python\)

```text
# restart service to flush your output buffer
# You can also flush manually, e.g. like this in python
import sys
print("Hello")
sys.stdout.flush()

# https://www.codegrepper.com/code-examples/assembly/journalctl+not+showing+all+logs
# https://stackoverflow.com/questions/10019456/usage-of-sys-stdout-flush-method

```

