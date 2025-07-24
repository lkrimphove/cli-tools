# scripts-and-tools

A collection of useful scripts and CLI tools for streamlining SAP CAP and general development workflows. This repository is intended as a personal toolbox to improve productivity, automate common tasks, and ensure consistency across local and deployed environments.

## Contents

- [`cf-pretty-logs`](#cf-pretty-logs) – Pretty-prints Cloud Foundry log output for better readability
- [`cf-deploy`](#cf-deploy) – Builds and deploys an SAP CAP application to Cloud Foundry using `mbt` and `cf deploy`

## Installation (Global Setup)

1. Create a local bin directory (if not already existing):

   ```bash
   mkdir -p ~/bin
   ```

2. Copy & paste the scripts you want to use and make them executable:

   ```bash
   chmod +x ~/bin/*
   ```

3. Add `~/bin` to your `PATH` (if not already):

   ```bash
   echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

## Contributions

If you have ideas or improvements, feel free to fork the repo and open a pull request.

---

## Scripts and Tools

### cf-pretty-logs

A CLI utility for pretty-printing and colorizing logs from Cloud Foundry. Ideal for improving readability of JSON-based logs in SAP CAP applications.

> [!WARNING]
> While there's room for further improvement, this already offers a significant upgrade over the default `cf logs` command.

#### Features

* Highlights log levels (INFO, WARN, ERROR)
* Displays timestamps and correlation/request IDs
* Gracefully handles non-JSON log lines
* Designed to be piped from `cf logs`

#### Example Usage

```bash
cf logs your-service | cf-pretty-logs
```

---

### cf-deploy

A script to build and deploy an SAP CAP application to Cloud Foundry with color-coded output, error handling, and an audible terminal bell on completion.

#### Features

* Runs `mbt build` to generate `mta.tar`
* Deploys with `cf deploy`
* Prints labeled sections for each step
* Exits early on failure
* Plays a terminal bell sound after completion

#### Example Usage

```bash
cf-deploy
```

> [!IMPORTANT]
> Prerequisites:
> * [`mbt`](https://sap.github.io/cloud-mta-build-tool/)
> * [`cf CLI`](https://docs.cloudfoundry.org/cf-cli/)