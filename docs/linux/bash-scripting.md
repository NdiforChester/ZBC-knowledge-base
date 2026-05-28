# Bash Scripting

Bash scripting is the practice of writing reusable command-line instructions in a file so Linux tasks can be automated. Bash is both an interactive shell and a scripting language.

DevOps engineers use Bash for deployments, backups, log checks, CI/CD steps, server setup, monitoring tasks, and quick automation. A useful rule is: if a task must be repeated, consider scripting it.

## 1. Why Bash Scripting Matters

Manual commands are useful for learning and troubleshooting, but they become risky when repeated often. Scripts improve:

- Speed.
- Consistency.
- Documentation of operational steps.
- Reduced human error.
- Reusable automation.

## 2. Your First Script

Create a file named `hello.sh`:

```bash
#!/usr/bin/env bash

echo "Hello from Bash"
```

Make it executable and run it:

```bash
chmod +x hello.sh
./hello.sh
```

The first line is called the shebang. It tells the system which interpreter should run the script.

## 3. Variables

Variables store values that can be reused.

```bash
server="prod-web-01"
port=8080

echo "Deploying to $server on port $port"
```

Important rule: do not add spaces around `=`.

Correct:

```bash
name="Ada"
```

Incorrect:

```bash
name = "Ada"
```

## 4. Command Substitution

Command substitution stores command output in a variable.

```bash
current_date=$(date)
current_user=$(whoami)

echo "Run by $current_user at $current_date"
```

## 5. User Input and Arguments

Interactive input:

```bash
read -r -p "Enter environment: " environment
echo "Selected environment: $environment"
```

Arguments passed when running a script:

```bash
#!/usr/bin/env bash

environment="$1"
service="$2"

echo "Deploying $service to $environment"
```

Run it:

```bash
./deploy.sh staging api
```

Useful argument variables:

| Variable | Meaning |
| --- | --- |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |

## 6. Conditionals

Conditionals allow scripts to make decisions.

```bash
#!/usr/bin/env bash

file="app.log"

if [ -f "$file" ]; then
  echo "$file exists"
else
  echo "$file does not exist"
fi
```

Common tests:

| Test | Meaning |
| --- | --- |
| `-f file` | File exists |
| `-d directory` | Directory exists |
| `-z string` | String is empty |
| `"$a" = "$b"` | Strings are equal |
| `$a -eq $b` | Numbers are equal |
| `$a -gt $b` | First number is greater |

## 7. Loops

For loop:

```bash
for file in *.log; do
  echo "Checking $file"
  grep "ERROR" "$file"
done
```

While loop:

```bash
count=1

while [ "$count" -le 5 ]; do
  echo "Attempt $count"
  count=$((count + 1))
done
```

Loops are useful for backups, log processing, retry logic, and running the same command across many files or servers.

## 8. Functions

Functions group reusable logic.

```bash
backup_file() {
  local file="$1"
  cp "$file" "$file.bak"
}

backup_file "/etc/hosts"
```

Functions make scripts easier to read, test, and maintain.

## 9. Safer Script Defaults

Use these options in scripts where failure should stop execution:

```bash
set -euo pipefail
```

Meaning:

- `-e`: exit when a command fails.
- `-u`: fail when using an undefined variable.
- `-o pipefail`: fail if any command in a pipeline fails.

## 10. Practical Example

```bash
#!/usr/bin/env bash
set -euo pipefail

service_name="$1"

if systemctl is-active --quiet "$service_name"; then
  echo "$service_name is running"
else
  echo "$service_name is not running"
  journalctl -u "$service_name" -n 20
fi
```

Run it:

```bash
./check-service.sh nginx
```

## 11. Best Practices

- Quote variables: use `"$name"` instead of `$name`.
- Use clear variable names.
- Validate required arguments.
- Avoid hardcoding secrets.
- Add comments only where logic is not obvious.
- Test scripts in a safe environment before production use.
- Use `shellcheck` when available.
