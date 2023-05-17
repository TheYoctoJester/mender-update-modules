## Description

The corrosion Update Module: implement a binary executable Update Module in Rust.

Example use-cases:

* Implementing proprietary logic or algorithms to process and apply an Artifacts payload.
* Together with the [Yocto recipe](https://github.com/mendersoftware/meta-mender-community/meta-mender-update-modules/recipes-mender/corrosion_git.bb) this provides a starting point to develop and ship custom Update Modules implemented in Rust.

### Specification

|||
| --- | --- |
|Module name| corrosion |
|Supports rollback|*note 1*|
|Requires restart|*note 1*|
|Artifact generation script|yes|
|Full system updater|*note 1*|
|Source code|[Update Module](https://github.com/mendersoftware/mender-update-modules/tree/master/corrosion/module/corrosion), [Artifact Generator](https://github.com/mendersoftware/mender-update-modules/blob/master/corrosion/module-artifact-gen/corrosion-artifact-gen)|

*note 1*: example flows are included

### Install the Update Module

Download the latest version of this Update Module by running:

```
git clone https://github.com/mendersoftware/mender-update-modules
cd mender-update-modules/corrosion/module
cargo build --release
sudo mkdir -p /usr/share/mender/modules/v3
sudo cp target/release/corrosion /usr/share/mender/modules/v3/corrosion
```

### Create artifact

To download `corrosion-artifact-gen`, run the following:

```
wget https://raw.githubusercontent.com/mendersoftware/mender-update-modules/master/corrosion/module-artifact-gen/corrosion-artifact-gen && chmod +x corrosion-artifact-gen
```

Generate Mender Artifacts using the following command:

```
ARTIFACT_NAME="my-update-1.0"
DEVICE_TYPE="my-device-type"
./corrosion-artifact-gen --artifact-name ${ARTIFACT_NAME} \
                         --device-type ${DEVICE_TYPE}
```

### Maintainer

The author and maintainer of this Update Module is:

- Josef Holzmayr - <josef.holzmayr@northern.tech>

Always include the original author when suggesting code changes to this update module.
