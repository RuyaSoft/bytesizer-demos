# Flights Application

This dataset contains airline customer data with their reward program membership status.

Before you start, please see this [README](../README.md) to set up Docker and pull the ByteSizer Docker image.

There is an input data file at `input_data/flight_rewards_data.csv` that originally contained 25,000 rows and we manually added 5 more containing some edge cases.
The data contains the following fields: `id, name, age, income, is_active, signup_date, tier`. 
`is_active` indicates whether a customer is currently an active user.
`tier` indicates the flight rewards program membership level originally with values `free, bronze, silver, gold`. 
We have added a new tier `platinum` and one representative row with that value considered as an edge for our purposes.
We have also added 4 more rows with anomalous values in the `age` and `income` columns again for the purpose of showcasing the edge case sampling capability of ByteSizer.

Example ByteSizer configuration files for each respective data are in the `configs` directory.

To run ByteSizer:
* Replace the `<file-name>` with one of the yaml file names in the `configs` directory and `<your-license-key>` with the license key provided to you.
* Run the following command at the parent of the `flight_rewards` directory based on your host system.

### Linux / MacOS
```shell
# You are in the bytesizer-demos directory
export BYTESIZER_LICENSE_KEY=<your-license-key>
docker run \
    -p 4200:4200 \
    -v $(PWD)/flight_rewards:/flight_rewards \
    -v $(PWD)/flight_rewards/logs:/logs \
    -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml \
    -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log \
    -e BYTESIZER_LICENSE_KEY=${BYTESIZER_LICENSE_KEY} \
    ruyasoft/bytesizer:beta
```

You could optionally keep your license key in the `.env` file located inside the `flight_rewards` directory by adding `BYTESIZER_LICENSE_KEY=<your-license-key>` and running the following command:
```shell
docker run \
    -p 4200:4200 \
    -v $(PWD)/flight_rewards:/flight_rewards \
    -v $(PWD)/flight_rewards/logs:/logs \
    --env-file flight_rewards/.env \
    -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml \
    -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log \
    ruyasoft/bytesizer:beta
```
You can also move any parameter specified with the `-e` flag to the `.env` file and remove the corresponding line from the command above.

### Windows 
```shell
# You are in the bytesizer-demos directory
docker run `
  -p 4200:4200 `
  -v "$(Get-Location)\flight_rewards:/flight_rewards \ `
  -v "$(Get-Location)\flight_rewards\logs:/logs" `
  --env-file flight_rewards\.env `
  -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml `
  -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log `
  ruyasoft/bytesizer:beta
```

