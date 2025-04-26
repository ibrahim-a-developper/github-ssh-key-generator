# SSH Key Generator GitHub Action

This GitHub Action generates an SSH key pair and outputs the public key. The private key is stored at the specified location, with a default path of `~/.ssh/id_rsa`. You can pass an email to personalize the key generation.

## Inputs

### `email`
**Required**  
The email address to associate with the SSH key. This is used to set the key comment.

### `path`
**Optional**  
The path where the private key will be saved. The default is `~/.ssh/id_rsa`.

## Outputs

This Action does not produce any direct outputs. However, the public key will be generated at the following location:
- `~/.ssh/id_rsa.pub` (or the custom path if specified).

## Example Usage

### Example 1: Using the Action in a Workflow

```yaml
jobs:
  generate-ssh-key:
    runs-on: ubuntu-latest
    steps:
      - name: Generate SSH Key
        uses: your-username/ssh-key-generator-action@v1
        with:
          email: "example@gmail.com"
          path: "~/.ssh/id_rsa"
