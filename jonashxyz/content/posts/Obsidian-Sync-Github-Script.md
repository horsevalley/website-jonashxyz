---
title : 'Obsidian Sync Github Script'
date : 2024-03-20T17:55:52+01:00
tags:
  - Article
  - script
  - sync
  - Git
  - bash
  - bash-script
  - shell-script
  - automation
  - resource
---
# obsidian-sync-github
## Why write this script?
I'm using Arch Linux and the Obsidian electron AppImage from AUR. It works great, but for some reason the obsidian git community plugin makes the app super sluggish. I removed the plugin and wrote my own bash script instead.
## How the script works
- Auto-pushes Obsidian notes to GitHub via a cronjob every 30 minutes
	- crontab -e -> `*/30 * * * * /home/jonash/.local/bin/obsidian-sync-github`
- Sends a notification via dunstify and your e-mail address of choice

```bash
#!/bin/bash

# Navigate to your repository directory
cd ~/obsidian/

# Add all changes to git
git add .

# Commit the changes with a current timestamp
git commit -m "Automated commit on $(date)"

# Push the changes
git push origin main

# Send notification after the push is sent
if git push origin main; then
  # Check if dunstify is available (dunst's notification tool)
  if command -v dunstify >/dev/null 2>&1; then
    # Send a notification
    dunstify "Successfully pushed obsidian notes to GitHub!"
  else
    echo "dunstify not found, cannot send notification"
  fi
  
  # Email details
  recipient="jonash@jonash.xyz"
  subject="Subject: Obsidian Notes Push Successful"
  body="Your Obsidian notes have been successfully pushed to GitHub on $(date)"
  
  # Send the email
  echo -e "$subject\n\n$body" | msmtp "$recipient"

else
  echo "git push failed"
fi
```
