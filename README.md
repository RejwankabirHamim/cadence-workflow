# cadence-workflow

https://cadenceworkflow.io/docs/get-started

## Install Cadence Service Locally

1. Run Cadence Server Using Docker Compose:
   ```bash
   git clone https://github.com/cadence-workflow/cadence.git
   cd cadence/docker && docker compose up
   ```
   Please keep this process running at background.
2. Register a Domain Using the CLI:
   ```bash
   docker run --network=host --rm ubercadence/cli:master --do test-domain domain register -rd 1
   ```
   Check that the domain is indeed registered:
   ```bash
   docker run --network=host --rm ubercadence/cli:master --do test-domain domain describe
   ```

## Run the worker

1. Run the following command to interact with your workflow:
   ```bash
   docker run --network=host --rm ubercadence/cli:master --domain test-domain workflow start --et 60 --tl test-worker --workflow_type main.helloWorldWorkflow --input '"World"'
   ```
2. Run your worker:
   ```bash
   go run main.go
   ```