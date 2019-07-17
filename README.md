# aws-secretsmanager-files

Writes AWS Secrets Manager secrets to files on disk.

<!-- TOC -->

- [Get it](#get-it)
- [Use it](#use-it)
  - [Examples](#examples)
- [Comments](#comments)

<!-- /TOC -->

## Get it

Using go get:

```bash
go get -u github.com/sgreben/aws-secretsmanager-files
```

Or [download the binary](https://github.com/sgreben/aws-secretsmanager-files/releases/latest) from the releases page.

```bash
# Linux
curl -L https://github.com/sgreben/aws-secretsmanager-files/releases/download/1.1.3/aws-secretsmanager-files_1.1.3_linux_x86_64.tar.gz | tar xz

# OS X
curl -L https://github.com/sgreben/aws-secretsmanager-files/releases/download/1.1.3/aws-secretsmanager-files_1.1.3_osx_x86_64.tar.gz | tar xz

# Windows
curl -LO https://github.com/sgreben/aws-secretsmanager-files/releases/download/1.1.3/aws-secretsmanager-files_1.1.3_windows_x86_64.zip
unzip aws-secretsmanager-files_1.1.3_windows_x86_64.zip
```

## Use it

```text

aws-secretsmanager-files [OPTIONS]

Usage of aws-secretsmanager-files:
  -file-mode uint
    	file mode for secret files (default 256)
  -secret FILE_PATH=SECRET_ARN
    	a key/value pair FILE_PATH=SECRET_ARN (may be specified repeatedly)
  -secret-json-key FILE_PATH=SECRET_ARN#JSON_KEY
    	a key/value pair FILE_PATH=SECRET_ARN#JSON_KEY (may be specified repeatedly)
  -secret-json-key-string FILE_PATH=SECRET_ARN#JSON_KEY
    	a key/value pair FILE_PATH=SECRET_ARN#JSON_KEY (may be specified repeatedly)
```

### Examples

```shell
$ aws-secretsmanager-files -secret ./secret.json=arn:aws:secretsmanager:eu-west-1:28381901202:secret:example-secret-1
$ cat ./secret.json
{"hello":"world"}

$ aws-secretsmanager-files -secret-json-key ./secret.json=arn:aws:secretsmanager:eu-west-1:28381901202:secret:example-secret-1#hello
$ cat ./secret.json
"world"

$ aws-secretsmanager-files secret-json-key-string ./secret.json=arn:aws:secretsmanager:eu-west-1:28381901202:secret:example-secret-1#hello
$ cat ./secret.json
world
```
