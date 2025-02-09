---
icon: material/bug
description: >-
  Learn about troubleshooting steps for common issues with deployKF.
---

# Troubleshooting

Learn about __troubleshooting steps__ for common issues with deployKF.

---

## Deployment Issues

!!! bug "Pods fail with "too many open files" error"

    ###### Pods fail with "too many open files" error:

    This error has been discussed in the upstream Kubeflow repo ([`kubeflow/manifests#2087`](https://github.com/kubeflow/manifests/issues/2087)), to resolve it, you will need to increase your system's open/watched file limits.

    On __linux__, you may need to increase the `fs.inotify.max_user_*` sysctl values:

    1. Modify `/etc/sysctl.conf` to include the following lines:
        - `fs.inotify.max_user_instances = 1280`
        - `fs.inotify.max_user_watches = 655360`
    2. Reload sysctl configs by running `sudo sysctl -p`