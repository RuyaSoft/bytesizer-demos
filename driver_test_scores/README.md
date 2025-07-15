# Driver Test Scores

This dataset simulates users with driver license test scores from different cities in the US. We have included one csv version and one json version for trying different functionalities of **ByteSizer**.

Files are in the `input_data` folder and example ByteSizer configuration files for each respective data are in the `configs` folder.

To run ByteSizer please run the following command at the parent of the `driver_test_scores` folder. Please first replace the \<FILE NAME\> with one of the yaml file names in the `configs` folder and \<YOUR LICENSE KEY\> with the license key provided to you:

### LINUX / MAC OS
```shell
# You are in the bytesizer-demos folder
docker run \
    -p 4200:4200 \
    -v $(PWD)/driver_test_scores:/driver_test_scores \
    -v $(PWD)/driver_test_scores/logs:/logs \
    -e YAML_CONFIG_FILE=/driver_test_scores/configs/<FILE NAME>.yaml \
    -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log \
    -e BYTESIZER_LICENSE_KEY=<YOUR LICENSE KEY> \
    ruyasoft/bytesizer:beta
```

You could optionally keep your license key in the `env` file located inside the `driver_test_scores` folder and run the following command:
```shell
# You are in the bytesizer-demos folder
docker run \
    -p 4200:4200 \
    -v $(PWD)/driver_test_scores:/driver_test_scores \
    -v $(PWD)/driver_test_scores/logs:/logs \
    --env-file driver_test_scores/env \
    -e YAML_CONFIG_FILE=/driver_test_scores/configs/<FILE NAME>.yaml \
    -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log \
    ruyasoft/bytesizer:beta
```
You can also move any parameter specified with the -e flag to the env file and remove the corresponding line from the command above.

### WINDOWS 
If you're using PowerShell you can run the multiline command by replacing \ line breaks with backticks ` and `$(PWD)` with `$(Get-Location)`
```shell
# You are in the bytesizer-demos folder
docker run `
  -p 4200:4200 `
  -v "$(Get-Location)\driver_test_scores:/driver_test_scores \ `
  -v "$(Get-Location)\driver_test_scores\logs:/logs" `
  --env-file driver_test_scores\env `
  -e YAML_CONFIG_FILE=/driver_test_scores/configs/<FILE NAME>.yaml `
  -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log `
  ruyaferit/bytesizer:multiarch
```
