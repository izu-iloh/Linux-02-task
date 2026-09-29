# Linux Command Line Practical Task — Command Workflow

Follow these commands in order in Kali Linux.

> Where a command requires an interactive action (such as `passwd` or `nano`), complete that action before continuing.

## STEP 1 — Create and Switch to a New User

```bash
sudo adduser student01
```

Set the requested password when prompted.

If sudo membership is required:

```bash
sudo usermod -aG sudo student01
```

Switch to the new user:

```bash
su - student01
```

Confirm the account:

```bash
whoami
```

Expected output:

```text
student01
```

## STEP 2 — Directory & File Management

Create the project and subdirectories:

```bash
mkdir -p ~/project/docs ~/project/scripts ~/project/bin
```

Move into `docs`:

```bash
cd ~/project/docs
```

Create `report.txt` with the required first line:

```bash
echo "This is the initial report by student01." > report.txt
```

View hidden files and directories:

```bash
ls -la
```

Create the hidden file:

```bash
echo "Top Secret." > .secret.txt
```

## STEP 3 — Edit and Move Files

Open `report.txt` with nano:

```bash
nano report.txt
```

Add this second line:

```text
Appended line using nano.
```

Save and exit nano.

Copy `report.txt` to `scripts`:

```bash
cp report.txt ../scripts/
```

Move `.secret.txt` to `bin` and rename it:

```bash
mv .secret.txt ../bin/classified.txt
```

Create `install.sh` in `scripts`:

```bash
cd ../scripts
nano install.sh
```

Enter exactly:

```bash
#!/bin/bash
echo "Installing project dependencies..."
```

Save and exit nano.

## STEP 4 — Permissions with chmod

In `scripts`, make `install.sh` executable by all users:

```bash
chmod a+x install.sh
```

In `bin`, remove read permission for others from `classified.txt`:

```bash
cd ../bin
chmod o-r classified.txt
```

In `docs`, create `admin_notes.txt`:

```bash
cd ../docs
touch admin_notes.txt
```

Set permission so only the owner can read and write:

```bash
chmod 600 admin_notes.txt
```

## STEP 5 — Clean-Up and Final Touches

Delete `admin_notes.txt`:

```bash
rm admin_notes.txt
```

Create the backup directory:

```bash
mkdir ../backup
```

Copy the entire contents of `docs` and `scripts` into `backup`:

```bash
cp -r . ../backup/docs
cp -r ../scripts ../backup/scripts
```

## Final Checks

Return to the home directory:

```bash
cd ~
```

Run:

```bash
tree project
```

If `tree` is not installed:

```bash
sudo apt install tree
```

Then run:

```bash
tree project
```

Use `ls -la` to confirm the required permissions and locations. Useful locations to inspect are:

```bash
ls -la project
ls -la project/docs
ls -la project/scripts
ls -la project/bin
ls -la project/backup
```

## Bonus — Optional

List the commands used:

```bash
history
```

Redirect history to the required file in the home directory:

```bash
history > ~/commands_used.txt
```
