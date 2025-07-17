# GitHub Collaboration Guide

## Create & Share the Repository

### GitHub Manager
- One person (the **GitHub Manager**) creates the repository on GitHub
- They go to: Repo → Settings → Collaborators
- Add team members by their GitHub username or email.
- Everyone else will get an **email or notification**, click **"Accept Invitation"**.

### Clone the Shared Repo
Once added, each teammate runs this in their terminal:

```bash
git clone <shared-repo-url>
cd <repo-folder>
```

## Install Dependencies & Set Up `.env`
### Install Node packages
- Inside the project folder:
```bash
npm install
``` 

### Create a `.env` file
```bash
touch .env
``` 
Inside .env, add your environment variables:
```bash
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/your-db-name
SESSION_SECRET=your_secret_key
PORT=3000
``` 
> ⚠️ Never commit .env to GitHub! Make sure it’s listed in your .gitignore.




## Branching & Code Workflow
### Branching Rules

- **Never code directly on the `main` branch.**
- Each team member should create their own feature branch before writing code.
- Follow a clear naming convention:

```bash
git checkout -b yourname-feature
```


## Daily Coding Workflow
1. Pull the Latest Changes from main
- Before you start any work, update your local main branch:
```bash
git checkout main
git pull origin main
```

2. Create or Switch to Your Feature Branch
- If you're starting a new feature:
```bash
git checkout -b yourname-feature
```

If you're continuing work on an existing branch:
```bash
git checkout yourname-feature
```

3. Make Code Changes and Commit Them
After editing files, save and commit your work:
```bash
git add .
git commit -m "Add: [brief description of change]"
```

> 💡 Use clear, consistent commit messages like:
> Add: register form UI
> Fix: navbar layout bug
> Update: form validation logic

4. Sync with Latest main (to Avoid Conflicts)
Before pushing, make sure your branch has the latest updates from main:
```bash
git checkout main
git pull origin main
git checkout yourname-feature
git merge main
```
 <details>
  <summary>‼️ How to Resolve Merge Conflicts </summary>

1. **Switch to `main` and pull the latest code**  
```bash
   git checkout main
   git pull origin main
```
Switch back to your feature branch
```bash
git checkout your-feature-branch
```
Merge main into your branch
```bash
git merge main
```
Open the conflicted files
Look for conflict markers like:
```bash
<<<<<<< HEAD
// your changes
=======
// incoming changes
>>>>>>> main
```
Manually edit the file to keep or combine code
Then delete the conflict markers.

Stage and commit the resolved file
```bash
git add .
git commit -m "Fix: resolved merge conflict"
```
Push your branch to GitHub
```bash
git push origin your-feature-branch
```
You can now finish your pull request as normal!
 </details>

5. Push Your Branch to GitHub
Once your code is ready:
```bash
git push origin yourname-feature
```

6. Open a Pull Request (PR)
Go to your GitHub repo.
Click "Compare & Pull Request".

Add:
- A clear title (e.g., Add login functionality)
- A short description of what you did
- Request a review from your teammates.

7. After Merging Your PR
Everyone on the team should update their local main:
```bash
git checkout main
git pull origin main
```

> ✅ Repeat this workflow for every new feature or fix!

