# terracamp ![Praise Be](/site/images/sun-praised.svg)

Boot-camp for Terraform.

A completely self-contained Terraform development environment.

## Getting Started

This project uses [Vagrant](https://vagrantup.com) and [VirtualBox](https://virtualbox.org) to provide a self-contained
development environment within a VM.

To bring up the machine:

```
$ vagrant up
```

Next, to shell into the machine:

```
$ vagrant ssh
```

You are now within the VM with all of the utilities installed.

## Usage

Usage diverges between various cloud providers. These are detailed presently.

### AWS

For AWS, the easiest way to get credentials to the VM is to simply export environment variables before shelling into the
VM:

```
$ export AWS_ACCESS_KEY_ID=abcdefg AWS_SECRET_ACCESS_KEY=hijklmnop
$ vagrant ssh
```

### GCP

For GCP, the `~/.config/gcloud` directory is mounted as a shared directory into the VM. This means that everything
should just work™, provided you are logged in already. If not, run the following command to log in:

```
$ gcloud auth login
```

This will emit a URL that you should open to generate authentication credentials for `gcloud`.

Next, from within the VM, the following environment variable should be exported to point to your credentials file for
the correct account.

```
$ vagrant ssh
$ export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcloud/legacy_credentials/me@mydomain.com/adc.json"
```

Additionally, if you'd like to bypass hardcoding in the Google compute region and project name, these can be exported
as environment variables as well. Remember to run this from within the VM:

```
$ export GOOGLE_PROJECT=myproject GOOGLE_REGION=us-east1
```

## License

Licensed at your discretion under either:

 - [MIT License](./LICENSE-MIT)
 - [Apache Software License, Version 2.0](./LICENSE-APACHE)
