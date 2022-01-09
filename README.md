# Vogsphere GitHub Actions

Sync your GitHub repository in Vogsphere automagically. Almost-GitOps pattern.

## About

Ever thought about not having to interact with Vogsphere and sync your GitHub files automatically? With GitHub Actions, you can!

This repository contains the files needed to set up a workflow that pushes your files whenever you push them to the GitHub main - or default - branch.

## Usage

There are some settings that need to be done in order for you to be able to use the workflow correctly in your repository:

### In your remote repository:

These steps need to be performed to set secret variables in your repository, like your repository address and your private key. Only then will the workflow be able to correctly interact with Vogsphere.

1. Have a GitHub repository.

2. Access your GitHub repository page.

3. Click `Settings` at the top.

4. Click `Secrets` at the left.

5. Click `New repository secret` at the top.

6. Add secret Name and Value (see following).

Repeat steps 5 and 6 to add these secrets:
 
1.
- Name: `VOGSPHERE_REPOSITORY_URL`
- Value: Your Vogsphere repository that you want to sync. You can get this in the project page in Intra. Ex: `git@vogsphere-v2.42sp.org.br:vogsphere/intra-uuid-x-x-x-x-x-x`

2.
- Name: `VOGSPHERE_URL`
- Value: Only the Vogsphere URL of your campus. You can get this in the `VOGSPHERE_REPOSITORY_URL` secret. Ex: `vogsphere-v2.42sp.org.br`

3. 
- Name: `VOGSPHERE_SSH_PRIVATE_KEY`
- Value: The private key related to the public key that you should set up in your Intra account. I recommend you create a new SSH key pair and set the public in your Intra account while using the private key here. Ex: `-----BEGIN OPENSSH PRIVATE KEY----- {KEY} -----END OPENSSH PRIVATE KEY-----`

### In your machine:

1. Identify the repository you want to use this workflow.

2. Access the repository folder in your machine.

3. In the path of your repository, clone this repository:

```bash
$ git clone git@github.com:caio-vinicius/vogsphere-github-actions.git
```

4. Create a folder `.github` with another folder `workflows` inside it.

```bash
$ mkdir -p .github/workflows
```

5. Move the `main.yaml` file to `.github/workflows` folder.

```bash
$ mv vogsphere-github-actions/main.yaml .github/workflows
```

6. Commit and push it to your remote repository. 

7. The workflow will run every time you push files into the main branch. For example, this time you push, if in main branch, the workflow should already work and push the files into the Vogsphere. You can check it in the "Actions" tab at the top of your repository page on GitHub.

8. Done!

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
