# Flight Rewards Application

**ByteSizer is a tool to create data subsets for testing, analytics, and machine learning workflows.**

[![Docker Pulls](https://img.shields.io/badge/docker-ready-blue)](https://github.com/orgs/ruyasoft/packages/container/package/bytesizer)

This dataset contains airline customer data with their reward program membership status.

Before you start, please see this [README](../README.md) to set up Docker and pull the ByteSizer Docker image.

There is an input data file at `input_data/flight_rewards_data.csv` that originally contained 25,000 rows and we manually added 5 more containing some edge cases.
The data contains the following fields: `id`, `name`, `age`, `income`, `is_active`, `signup_date`, `tier`.

**Sample Data Row:**
```
id,name,age,income,is_active,signup_date,tier
1001,Jane Doe,34,75000,True,2021-03-15,silver
```

`is_active` indicates whether a customer is currently an active user.
`tier` indicates the flight rewards program membership level originally with values `free`, `bronze`, `silver`, `gold`.
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
    -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log \
    -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml \
    -e BYTESIZER_LICENSE_KEY=${BYTESIZER_LICENSE_KEY} \
    ghcr.io/ruyasoft/bytesizer:beta
```

You could optionally keep your license key in the `.env` file located inside the `flight_rewards` directory by adding `BYTESIZER_LICENSE_KEY=<your-license-key>` and running the following command:
```shell
docker run \
    -p 4200:4200 \
    -v $(PWD)/flight_rewards:/flight_rewards \
    -v $(PWD)/flight_rewards/logs:/logs \
    -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log \
    --env-file flight_rewards/.env \
    -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml \
    ghcr.io/ruyasoft/bytesizer:beta
```
You can also move any parameter specified with the `-e` flag to the `.env` file and remove the corresponding line from the command above.

### Windows
> **Note:** The following command is intended for use in **PowerShell**. The backtick character (\`) at the end of each line is used for line continuation in PowerShell. If you are using Command Prompt (cmd.exe), you will need to adjust the syntax accordingly.

```shell
# You are in the bytesizer-demos directory
docker run `
  -p 4200:4200 `
  -v "$(Get-Location)\flight_rewards:/flight_rewards" `
  -v "$(Get-Location)\flight_rewards\logs:/logs" `
  -e LOG_FILE=/flight_rewards/logs/bytesizer-test.log `
  --env-file flight_rewards\.env `
  -e YAML_CONFIG_FILE=/flight_rewards/configs/<file-name>.yaml `
  ghcr.io/ruyasoft/bytesizer:beta
```

## License

This project is licensed under the terms described in the [LICENSE](LICENSE.txt) file.

## Need Help?

Open an issue or contact us at support@bytesizer.ai.
