# AWS AMI for CSYE 6225

## Validate Template

```sh
packer validate ubuntu-ami.json
```

## Build AMI

```sh
packer build \
    -var 'aws_access_key=REDACTED' \
    -var 'aws_secret_key=REDACTED' \
    -var 'aws_region=us-east-1' \
    -var 'subnet_id=REDACTED' \
    ubuntu-ami.json
```

or 

```
packer build -var-file=./vars.json ubuntu-ami.json
```

## CentOS/Red Hat Packer Conflict

Ref: https://github.com/hashicorp/packer/issues/1117#issuecomment-379270051

if you getting error like this in linux machines
```
/usr/share/cracklib/pw_dict.pwd: Permission denied
/usr/share/cracklib/pw_dict: Permission denied
```

### try this method it will work
download the package
unzip it

### move the file to /usr/local/
```
$ mv /path/packer /usr/local/
```

### setting the packer path
```
vi ~/.bashrc
export PATH=$PATH:/usr/local/
source ~/.bashrc
```

### linux machines already have a packer name package so you need to link the hash corp packers
```
sudo ln -s /usr/local/packer /usr/bin/packer.io
```

### your packer is ready
```
packer.io
```

See https://github.com/hashicorp/packer/issues/1117
