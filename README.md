# instance-cloudimage

## Design Guidelines

This OS provider should provide users with an easy way of creating Ganeti Instances from simple blockdevice images using the [Ganeti OS Interface](https://docs.ganeti.org/docs/ganeti/3.0/html/man-ganeti-os-interface.html).

### Image Sources and Formats

Images should be accessible through a local filesystem path or can be retrieved from HTTP(S) URLs. An OS image may be available in different formats (e.g. raw, compressed raw, qcow2, vdi or others) and will be converted to native blockdevice data by this OS provider. 

It is expected that the image contains a system supported by [cloud-init](https://cloud-init.io/) which does take care of e.g. expanding the root filesystem to the full disk size upon first boot and also configure basic elements like networking.

Configuration details of the instance itself should be retrieved from Ganeti's metadata-daemon (`metad`). This may require modification of Ganeti itself, which will be documented here if needed.

### Variants

TBD

### Variant Parameters

TBD

### OS Parameters

TBD

### Hooks

The OS provider may implement a hook system which lets users add additional steps to the provisioning process. Hooks may be executed _before_ the image is downloaded/opened/converted or _after_ it has been written to the blockdevice. 

### Programming Language

This OS provider could be implemented in any language which supports the Ganeti OS Interface. However, it should be a language widely supported by current and common Linux Distributions and also provide an easy way to test the code. Python 3 along with pytest would be in line with the Ganeti codebase, but it is not a requirement.
