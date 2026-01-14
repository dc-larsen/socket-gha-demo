# Socket GitHub Actions Scanning Demo

Verify that Socket's GitHub Actions scanning is working on your organization.

## What This Demo Does

This repository contains a simple workflow using standard GitHub Actions (`actions/checkout`, `actions/setup-node`). Socket's GitHub App scans the workflow and surfaces the behaviors these actions perform.

Learn more about GitHub Actions scanning: [Introducing GitHub Actions Scanning Support](https://socket.dev/blog/introducing-github-actions-scanning-support)

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

### 4. Clear the default filter

**Important:** Socket applies a default filter that hides low-priority alerts. You'll see "No alerts found" until you clear it.

Look for the filter chip near the search bar (e.g., "Alert Action is 3 actions") and click the **X** to remove it. You should then see the alerts listed below.

## Expected Results

After clearing the filter, you should see alerts like:

| Alert | Action | What it means |
|-------|--------|---------------|
| System shell access | actions/checkout | Action executes shell commands |
| Dynamic code execution | actions/checkout | Action runs dynamically generated code |
| Network access | actions/checkout | Action makes network requests |
| System shell access | actions/setup-node | Action executes shell commands |
| Dynamic code execution | actions/setup-node | Action runs dynamically generated code |
| Network access | actions/setup-node | Action makes network requests |
| Filesystem access | actions/checkout | Action reads/writes files |
| Environment variable access | actions/setup-node | Action accesses environment variables |

These are **low-priority informational alerts** showing Socket is analyzing what your GitHub Actions do. In production, Socket flags malicious or typosquat actions at higher severity.

## What This Confirms

If you see these alerts, GitHub Actions scanning is working correctly on your org. Socket will now monitor all workflow files for:

- Known malicious actions
- Typosquat actions (e.g., `actinos/checkout` instead of `actions/checkout`)
- Suspicious behaviors and supply chain risks

## Cleanup

After verifying, you can keep or delete the forked repository.

## Questions?

Contact your Socket account team or email support@socket.dev.
