## Install InstructLab

### Remove the default libs in venv
By running this command
```shell
python3 -m venv venv
source venv/bin/activate
```
A new virtual environment is created which includes all the libs install in your local machine! It's better to remove them from virtual environment first
```shell
pip freeze | xargs pip uninstall -y
```

## Install InstructLab for mac
```shell
pip install 'instructlab[mps]'
```

## Run ilab
From your venv environment, verify ilab is installed correctly, by running the ilab command.
```shell
ilab
```
and you should see
```shell
Usage: ilab [OPTIONS] COMMAND [ARGS]...

  CLI for interacting with InstructLab.

  If this is your first time running ilab, it's best to start with `ilab
  config init` to create the environment.

Options:
  --config PATH  Path to a configuration file.  [default:
                 /Users/bahram/.config/instructlab/config.yaml]
  -v, --verbose  Enable debug logging (repeat for even more verbosity)
  --version      Show the version and exit.
  --help         Show this message and exit.

Commands:
  config    Command Group for Interacting with the Config of InstructLab.
  data      Command Group for Interacting with the Data generated by...
  model     Command Group for Interacting with the Models in InstructLab.
  system    Command group for all system-related command calls
  taxonomy  Command Group for Interacting with the Taxonomy of InstructLab.

Aliases:
  chat      model chat
  generate  cli data
  serve     cli model
  train     cli model
  ```

## Initialize ilab
https://docs.instructlab.ai/getting-started/initilize_ilab/ 
Initialize ilab by running the following command:
```shell
ilab config init
```
### Important directories
```shell
Path to taxonomy repo [/<HOME_DIR>/.local/share/instructlab/taxonomy]
Path to your model [/<HOME_DIR>/.cache/instructlab/models/]
Generating config file [<HOME_DIR>/.config/instructlab/config.yaml]
```
```
├─ ~/.cache/instructlab/models/ (1)
├─ ~/.local/share/instructlab/datasets (2)
├─ ~/.local/share/instructlab/taxonomy (3)
├─ ~/.local/share/instructlab/checkpoints (4)
```
1) ~/.cache/instructlab/models/: Contains all downloaded large language models, including the saved output of ones you generate with ilab.

2) ~/.local/share/instructlab/datasets/: Contains data output from the SDG phase, built on modifications to the taxonomy repository.

3) ~/.local/share/instructlab/taxonomy/: Contains the skill and knowledge data.

4) ~/.local/share/instructlab/checkpoints/: Contains the output of the training process
   
   
## Download Model
https://docs.instructlab.ai/getting-started/download_models/

By running this command
```shell
ilab model download
```
ilab model download downloads a compact pre-trained version of the model (~4.4G) from HuggingFace:
```
Downloading model from Hugging Face: instructlab/merlinite-7b-lab-GGUF@main to /<HOME_DIR>/.cache/instructlab/models...
```
Run this command to list the models
```shell
ilab model list
```
```
+------------------------------+---------------------+--------+
| Model Name                   | Last Modified       | Size   |
+------------------------------+---------------------+--------+
| merlinite-7b-lab-Q4_K_M.gguf | 2024-11-06 20:57:15 | 4.1 GB |
+------------------------------+---------------------+--------+
```
### Download Granite
```shell
ilab model download -rp instructlab/granite-7b-lab
```

## Serving a model
https://docs.instructlab.ai/getting-started/serve_and_chat/  


To serve the default model
```shell
ilab model serve
```

### Chat with specific GGUF 
Download Granite GGUF from Huggingface
```
https://huggingface.co/instructlab/granite-7b-lab-GGUF/tree/main
```
then run this command
```shell
ilab model chat /<HOME_DIR>/.cache/instructlab/models/granite-7b-lab-Q4_K_M.gguf
```
