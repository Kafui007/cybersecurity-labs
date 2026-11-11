# Lab 06 — Using John the Ripper to crack passwords

John the Ripper is one of the more powerful password-cracking tools. This lab
hashes a known password, then cracks it.

## Step 1 — Create a password hash file

```bash
echo "password123" | openssl passwd -6 > hashed_password.txt
```

## Step 2 — Run John the Ripper

```bash
john hashed_password.txt
```

## Step 3 — Monitor the progress

Press Enter while John is running to check the status of the cracking process.

## Step 4 — View results

```bash
john --show hashed_password.txt
```

## Takeaway

`password123` — one of the most common passwords in every breach dataset — falls
immediately to a dictionary attack. The lesson is the defence: long, unique
passwords (or a password manager) and, on the server side, slow hashing algorithms
and lockout policies so that a stolen hash file is not a free pass.
