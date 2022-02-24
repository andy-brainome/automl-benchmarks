<!--
# Brainome Daimensions(tm)
#
# The Brainome Table Compiler(tm)
# Copyright (c) 2022 Brainome Incorporated. All Rights Reserved.
# GPLv3 license, all text above must be included in any redistribution.
# See LICENSE.TXT for more information.
#
# This program may use Brainome's servers for cloud computing. Server use
# is subject to separate license agreement.
#
# Contact: itadmin@brainome.ai
# for questions and suggestions.
#
# @author: andy.stevko@brainome.ai
# @author: zachary.stone@brainome.ai
-->

# brainome/automl-benchmarks
ML benchmarks comparing brainome, google, sage maker, and azure engines

## Installation / Setup

```bash
echo "clone source"
git clone git@github.com:andy-brainome/snowflake_proof.git
cd snowflake_proof

echo "create/activate virtual env and install dependencies"
python3 -m venv venv3810
source venv/bin/activate
python3 -m pip install -U pip
python3 -m pip install -r requirements.txt
sudo apt install unzip

echo "brainome key required for large files"
brainome login

echo "install aws cli e.g. python3 -m pip install awscli"

echo "create azure resources"

echo "\nsetup google vertex env at https://cloud.google.com/vertex-ai/docs/start/cloud-environment"
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-374.0.0-linux-x86_64.tar.gz
tar -xf google-cloud-sdk-374.0.0-linux-x86.tar.gz
./google-cloud-sdk/install.sh
./google-cloud-sdk/bin/gcloud init
echo "settings required for install three clouds"
vim helpers/user_variable.py


echo 'downloading data from open ml into /Dropbox/Open_ML-Data/'
mkdir -f "/Dropbox/Open_ML-Data/"
python3 opem_ml_download_data.py
```

## Initialization
Specify snowflake credentials and other configuration in config.py
```python
credentials = ['<username>', '<password>', '<account>']
warehouse = database = schema = "<whatevers>"
```
## Demonstrations
### Usage
python3 open_ml_experiement.py <tool_name> <suite_tsv_file> <data_dir>

### Running brainome benchmark
python3 open_ml_brainome_wrapper.py test-suites/open_ml_select.tsv /Dropbox/OpenML-Data/

### Running open_ml_experiment
```bash
python3 open_ml_experiement.py sagemaker test-suites/open_ml_select.tsv /Dropbox/OpenML-Data/
```

### Results and Predictions
	RESULT_DIR = f"{tool}-runs"
	PREDICTIONS_DIR = f"{tool}-predictions"