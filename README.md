
## Poplar Installation on an GraphCore IPU POD

Steps to Install Poplar SDK on a IPU POD (provided you have access to IPU Hardware)

### Step 1 - Connect to your IPU POD via SSH

Connect to the IPU POD via SSH

```bash
ssh username@mentioned_by_the_authorities.graphcloud.ai
```

This will log you into your user space

### Step 2 - Download the GraphCore SDK

You will have to manually install the Poplar SDK in the IPU POD to further experiment with codes or take Poplar for a test run

Head to [https://downloads.graphcore.ai/](https://downloads.graphcore.ai/)

You’ll be asked to sign in (you can do so if you have access to the GraphCore hardware)

Select the relevant Poplar SDK version based on the Platform and version you need

You need to download the compressed tarball file to the host PC and then transfer it to the remote server via SCP

Use the following piece of code to do so successfully

```bash
scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2:.
```

Example:

```bash
scp /Users/narenkhatwani/Downloads/poplar_sdk-ubuntu_18_04-2.4.0-d16ca54529.tar.gz username@mentioned_by_the_authorities.graphcloud.ai:.
```

### Step 3 - Head to your IPU POD User Space and install the Poplar SDK

Use the following command to unpack the tarball file

```bash
tar -xvzf poplar_sdk-[os]-[ver].tar.gz
```

### Step 4 - Setup the ****SDK environment****

To use the Graphcore tools and Poplar libraries use the following commands

```bash
cd poplar_sdk-[os]-[ver]
source poplar-[os]-[ver]/enable.sh
source popart-[os]-[ver]/enable.sh
```

### Step 5 - Verify your Poplar installation

```bash
popc --version
```

### Step 6 - Take Poplar for a test run with the “Hello World Program”

```bash
poprun --num-instances 2 --num-replicas 2 --offline-mode=1 echo "Hello world!"
```

If the installation is done properly you should get Hello World printed two times as there are two instances running

**Output:**

```bash
Hello world!
Hello world!
```