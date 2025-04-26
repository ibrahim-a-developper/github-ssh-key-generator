# SSH Key Generator - GitHub Action

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-ready-blue)
![License](https://img.shields.io/github/license/ibrahim-a-developper/github-ssh-key-generator)

A GitHub Action that generates SSH key pairs (RSA/ed25519) for use in your workflows. Perfect for automating deployments, server access, or any task requiring SSH authentication.

## Features

- 🔐 Generate RSA (default) or ed25519 SSH keys
- ⚙️ Customizable key strength (bits for RSA)
- 📁 Automatic key storage in `$HOME/.ssh/`
- 🔑 Optional passphrase protection
- 📋 Public key output in workflow logs

## Usage

### Basic Example

```yaml
steps:
  - uses: ibrahim-a-developper/github-ssh-key-generator@v1
    with:
      email: 'your-email@example.com'
```

### Advanced Example

```yaml
steps:
  - uses: ibrahim-a-developper/github-ssh-key-generator@v1
    with:
      email: 'ci@your-org.com'
      key_type: 'ed25519'  # or 'rsa'
      bits: '4096'         # for RSA keys
      filename: 'github_actions_key'
      passphrase: '${{ secrets.SSH_PASSPHRASE }}'
```

## Inputs

| Parameter    | Required | Default | Description |
|-------------|----------|---------|-------------|
| `email`     | Yes      | -       | Email to associate with the key |
| `key_type`  | No       | `rsa`   | Key type (`rsa` or `ed25519`) |
| `bits`      | No       | `4096`  | Key strength (for RSA only) |
| `filename`  | No       | `id_rsa`| Key filename (without path) |
| `passphrase`| No       | `""`    | Key passphrase (empty for none) |

## Outputs

The action will:
1. Generate a key pair in `$HOME/.ssh/`
2. Print the public key in the workflow logs
3. Set appropriate permissions (600 for private key)

## Security Notes

🔒 **Important Security Considerations:**
- Never commit private keys to your repository
- Consider using GitHub Secrets for passphrases
- Generated keys persist only for the workflow duration (ephemeral runners)
- For production use, consider using GitHub's built-in deploy keys instead

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

Found a bug or have a feature request? [Open an issue](https://github.com/ibrahim-a-developper/github-ssh-key-generator/issues).

---

✨ **Pro Tip:** Combine this with the [SSH Agent Action](https://github.com/webfactory/ssh-agent) for complete SSH key management in your workflows!
