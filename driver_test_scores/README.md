# Driver Test Scores

This dataset contains information about users with driver license test scores from different cities in the US. There is a csv version and a json version of the same dataset to try **ByteSizer**.

Before you start, please see this [README](../README.md) to set up Docker and pull the ByteSizer Docker image.

Files are in the `input_data` directory and example ByteSizer configuration files for each respective dataset file are in the `configs` directory.

To run ByteSizer:
* Replace the `<file-name>` with one of the yaml file names in the `configs` directory and `<your-license-key>` with the license key provided to you.
* Run the following command at the parent of the `driver_test_scores` directory based on your host system.

### Linux / MacOS
```shell
# You are in the bytesizer-demos directory
export BYTESIZER_LICENSE_KEY=<your-license-key>
docker run \
    -p 4200:4200 \
    -v $(PWD)/driver_test_scores:/driver_test_scores \
    -v $(PWD)/driver_test_scores/logs:/logs \
    -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log \
    -e YAML_CONFIG_FILE=/driver_test_scores/configs/<file-name>.yaml \
    -e BYTESIZER_LICENSE_KEY=${BYTESIZER_LICENSE_KEY} \
    ghcr.io/ruyasoft/bytesizer:beta
```

You could optionally keep your license key in the `.env` file located inside the `driver_test_scores` directory and running the following command:
```shell
# You are in the bytesizer-demos directory
docker run \
    -p 4200:4200 \
    -v $(PWD)/driver_test_scores:/driver_test_scores \
    -v $(PWD)/driver_test_scores/logs:/logs \
    --env-file driver_test_scores/.env \
    -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log \
    -e YAML_CONFIG_FILE=/driver_test_scores/configs/<file-name>.yaml \
    ghcr.io/ruyasoft/bytesizer:beta
```
You can also move any parameter specified with the `-e` flag to the `.env` file and remove the corresponding line from the command above.

### Windows 
```shell
# You are in the bytesizer-demos directory
docker run `
  -p 4200:4200 `
  -v "$(Get-Location)\driver_test_scores:/driver_test_scores" `
  -v "$(Get-Location)\driver_test_scores\logs:/logs" `
  -e LOG_FILE=/driver_test_scores/logs/bytesizer-test.log `
  --env-file driver_test_scores\.env `
  -e YAML_CONFIG_FILE=/driver_test_scores/configs/<file-name>.yaml `
  ghcr.io/ruyasoft/bytesizer:beta
```
