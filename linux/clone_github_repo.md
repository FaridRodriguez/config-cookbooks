# Clone GitHub repo using ssh key on linux

1. **Generate an SSH key** (if you don't have one already):
   ```
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

2. **Add the SSH key to the ssh-agent**:
   ```
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```

3. **Add the SSH key to your GitHub account**:
   - Copy the SSH key to your clipboard:
     ```
     cat ~/.ssh/id_rsa.pub
     ```
   - Go to GitHub, navigate to **Settings > SSH and GPG keys > New SSH key**, and paste the key.

4. **Clone the repository using SSH**:
   ```
   git clone git@github.com:username/repository.git
   ```

Replace `username` and `repository` with the appropriate GitHub username and repository name.