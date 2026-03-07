# GitHub Actions Migration TODO

## GitHub Repository Configuration

### 1. Configure GitHub Secrets
Navigate to: Settings → Secrets and variables → Actions → New repository secret

Add the following secrets:
- [#] `GPG_PRIVATE_KEY` - Your GPG private key for signing artifacts
- [#] `GPG_PASSPHRASE` - Passphrase for the GPG key
- [#] `GPG_KEYNAME` - The GPG key ID/name
- [#] `CENTRAL_USERNAME` - Maven Central username (Sonatype token username)
- [#] `CENTRAL_PASSWORD` - Maven Central password/token
- [ ] `RELEASE_PLEASE_TOKEN` - Personal Access Token (classic) with `repo` scope to allow release-please to trigger other workflows

### 2. Push Migration Branch
- [#] Push the `github-actions-migration` branch to GitHub
  ```bash
  git push -u origin github-actions-migration
  ```

### 3. Create Pull Request
- [#] Create PR from `github-actions-migration` to `main`
- [#] Verify the Build workflow runs successfully on the PR
- [#] Review and merge the PR

### 4. Verify GitHub Actions is Working
- [#] Check that Release-Please creates a release PR for version 0.0.38
- [#] Merge the release PR
- [X] Verify Deploy workflow runs and publishes to Maven Central
- [X] Check that release is created and tagged

### 5. Pause/Remove Concourse Pipeline
- [#] Pause the `movealong-oss` pipeline in Concourse
- [ ] Once confident in GitHub Actions, remove the Concourse pipeline entirely

## Optional Configuration

### Branch Protection (if desired)
Navigate to: Settings → Branches → Add branch protection rule for `main`
- [ ] Require pull request reviews before merging
- [ ] Require status checks to pass (select Build workflow)
- [ ] Require branches to be up to date before merging

### Notifications (if desired)
Navigate to: Settings → Notifications
- [ ] Configure notification preferences for workflow runs
