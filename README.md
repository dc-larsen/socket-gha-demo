# Socket GitHub Actions Scanning Demo

Verify that Socket's GitHub Actions scanning is working on your organization.

## What This Demo Does

This repository contains a simple workflow using standard GitHub Actions (`actions/checkout`, `actions/setup-node`). Socket's GitHub App scans the workflow and surfaces the behaviors these actions perform.

## Setup Instructions

### 1. Fork this repository

Click **Fork** in the top right to create a copy in your organization.

### 2. Verify Socket's GitHub App is installed

Go to your org's GitHub settings:
```
https://github.com/organizations/YOUR-ORG/settings/installations
```

Confirm the Socket app is installed and has access to the forked repo.

### 3. Check Socket Dashboard

1. Go to [socket.dev/dashboard](https://socket.dev/dashboard)
2. Select your organization
3. Navigate to **Scans** and find the forked repo
4. Click into the scan to view alerts

## Expected Results

You should see alerts for behaviors like:

| Alert | Action | What it means |
|-------|--------|---------------|
| System shell access | actions/setup-node | Action executes shell commands |
| Dynamic code execution | actions/setup-node | Action runs dynamically generated code |
| Network access | actions/setup-node | Action makes network requests |
| Filesystem access | actions/setup-node | Action reads/writes files |

These are **low-priority informational alerts** showing Socket is analyzing what your GitHub Actions do. In production, Socket flags malicious or typosquat actions at higher severity.

## What This Confirms

If you see these alerts, GitHub Actions scanning is working correctly on your org. Socket will now monitor all workflow files for:

- Known malicious actions
- Typosquat actions (e.g., `actinos/checkout` instead of `actions/checkout`)
- Suspicious behaviors and supply chain risks

## Cleanup

After verifying, you can keep or delete the forked repository.

## Questions?

Contact your Socket account team.
