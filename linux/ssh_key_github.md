 ## Add a SSH key to github
 
 To add a new SSH key to GitHub, follow these steps:

1. **Generate a new SSH key:**
    - Open a terminal and run the following command, replacing `your_email@example.com` with your GitHub email address:
      ```sh
      ssh-keygen -t ed25519 -C "your_email@example.com"
      ```
    - If you are using an older system that doesn't support `ed25519`, you can use `rsa`:
      ```sh
      ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
      ```

    - When prompted to "Enter a file in which to save the key," you can press Enter to accept the default file location (`~/.ssh/id_ed25519` or `~/.ssh/id_rsa`).

    - When prompted, enter a secure passphrase (or leave it empty for no passphrase).

2. **Add the SSH key to the SSH agent:**
    - Start the SSH agent in the background:
      ```sh
      eval "$(ssh-agent -s)"
      ```

    - Add your SSH private key to the SSH agent:
      ```sh
      ssh-add ~/.ssh/id_ed25519
      ```
      or
      ```sh
      ssh-add ~/.ssh/id_rsa
      ```

3. **Copy the SSH key to your clipboard:**
    - Use the following command to copy the SSH key to your clipboard:
      ```sh
      cat ~/.ssh/id_ed25519.pub | xclip -selection clipboard
      ```
      or
      ```sh
      cat ~/.ssh/id_rsa.pub | xclip -selection clipboard
      ```

    - If `xclip` is not installed, you can install it using:
      ```sh
      sudo apt-get install xclip
      ```

4. **Add the SSH key to your GitHub account:**
    - Go to [GitHub's SSH and GPG keys settings page](https://github.com/settings/keys).
    - Click on "New SSH key" or "Add SSH key".
    - In the "Title" field, add a descriptive label for the new key (e.g., "My Laptop SSH Key").
    - Paste the SSH key into the "Key" field.
    - Click "Add SSH key".

5. **Test the SSH connection:**
    - Run the following command to test the SSH connection to GitHub:
      ```sh
      ssh -T git@github.com
      ```

    - You should see a message like:
      ```sh
      Hi username! You've successfully authenticated, but GitHub does not provide shell access.
      ```

This confirms that your SSH key has been successfully added to your GitHub account and you can now use SSH for Git operations.