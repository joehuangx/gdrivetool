# Google Drive Upload/Download Tool

***It's a command-line tool let you easily upload and download files.***

## Feature

+ **Upload :**

  + Upload into a newly-created directory
  + Upload into an existing directory
  + Upload into a newly-created directory in an existing directory
+ **Download :**

  + Download files and directories into a designated local path
+ **List :**

  + Display metadata of files under a designated directory and stored info into `list.json`

## Instruction

### 1. Prerequisite

+ Python 3 or above
+ pip or pip3 is installed

### 2. Create credentials

Visit [Google Developers Console](https://console.developers.google.com/) and apply for the credentials.

After set up successfully, choose option to download it as JSON format and save it into your local space.

( You can follow this direction : [建立憑證](./建立憑證.pdf) )

### 3. Install required modules

Please install with the command :

```python
$ pip install -r requirements.txt
or 
$ pip3 install -r requirements.txt
```

( Depends on your version `pip` or `pip3` )

### 4. How to use the tool

You can follow this direction : [使用手冊](./使用手冊.pdf) or read the following simple instructions.

**Typical structure :**

```python
$ python -m gdrivetool [function] {[arg1] [arg2]...}
```

#### (1) Authenticate / Update content of API

For the first time, please authenticate gdrive API and a new file named `token.pickle` will automatically be created with the following command.

```python
$ python -m gdrivetool auth -cred '{/path/to/yourcredentials.json}'
```

+ Introduction to arguments :

  + `auth` : choose authenticate function

    Options :

    + `-cred` (Required): personal OAuth 2.0 credential file with format of JSON

( If you want to change different account to download or uplaod, just execute above command again. )

#### (2) Upload

```python
$ python -m gdrivetool upload '{Options}'
```

+ Introduction to arguments :

  + `upload` : choose upload function

    Options :

    + `-src` (Required) : full path or relative path to source file or directory to upload
    + `-new` (Optional) : new folder name you wanna create into gdrive
    + `-dest` (Optional) : destination directory id/url in gdrive where you wanna upload into

    ( Input more than one path at one time is permitted and _remember to separate different path by "whitespace_" )

    > For example :
    >

    ```python
    $ python -m gdrivetool upload -src '{/path/to/file}' '{/path/to/folder}' -new '{foldername}' -dest '{directoryid/url}'
    ```

#### (3) Download

```python
$ python -m gdrivetool download '{Options}'
```

+ Introduction to arguments :

  + `download` : choose download function

    Options :

    + `-src` (Required) : multiple gdrive ids/urls
    + `-dest` (Required) : path/to/local/directory as download destination
    + `-c` (Optional) : Update all files and folders with the same name without more request

    ( Allowed to add more than one id or url at one time and remember to separate different ones by "whiteapce" )

    > For example :
    >

    ```python
    $ python -m gdrivetool download -src '{fileid}' '{directoryurl}'... -dest '{/path/to/localdirectory}' -c
    ```

#### (4) List (retrieve all metadata under the given directory id)

```python
$ python -m gdrivetool list -src '{gdrive folder url/id}'
```

+ Introduction to arguments :

  + `list` : choose list function

    Options :

    + `-src` (Required) : directory id/url ( input one at one time )

#### NOTE:

+ If you execute on `zsh` with urls, to quote your url will be necessary.
