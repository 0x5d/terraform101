# Terraform 101

A basic terraform example for a Medellin DevOps meetup talk, based on
[this example](https://github.com/hashicorp/terraform/blob/master/examples/aws-two-tier/).

You can find the accompanying slides here: http://slides.com/castillobgr/terraform101

## Setup

- Clone this repo
  ```
  git clone https://github.com/castillobg/blue-green.git
  ```

- Create a key pair for the EC2 instances we'll create. Run `ssh-keygen` and follow the steps.

- Inside `/blue-green/terraform/` create a `secrets.tfvars` file with your AWS credentials:
  ```
  cat <<EOF > variables.tfvars
  access_key = "<your access key>"
  secret_key = "<your secret key>"
  public_key_path = "<path to the public key you generated>"
  private_key_path = "<path to the private key you generated>"
  key_name = "<a name for the key>"
  EOF
  ```
  Optionally, you can include an ami_code entry if you want to use a different one, like so:
  `ami_code = "<ami code>"`. Default is [`ami-408c7f28`]().

  Please note quotation marks ("") are mandatory for all entry values!

- Run `$ terraform plan -var-file=variables.tfvars` and review the steps Terraform will follow to
spin up your infrastructure.

- **NOTICE:** if your account is not eligible AWS's free tier, you will be charged some money for
running this step, which creates actual resources. **If you're sure**, run `$ terraform apply`.

- Watch Terraform do its magic!
