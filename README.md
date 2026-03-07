# Hello World Node.js App

This is a simple Node.js application that prints "hello world" to the console.

## Installation

Run `npm install` to install dependencies (none in this case).

## Running

Run `npm start` or `node index.js` to execute the program.

## Docker

To build and run with Docker:

```bash
docker build -t hello-world .
docker run hello-world
```

## CI/CD with GitHub & ECR

A GitHub Actions workflow is provided to build the image, push to Amazon ECR, and tag it by commit SHA. Create the following secrets in your repository settings:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION` (e.g. `us-east-1`)

Workflow file: `.github/workflows/ecr-publish.yml` will trigger on pushes to `main`. The pipeline:

1. Checkout source
2. Configure AWS credentials
3. Login to ECR
4. Build, tag, and push Docker image

After a successful run the image URI is echoed in the actions log.

The image will be available in your AWS ECR repository `hello-world` with the tag matching the commit SHA.