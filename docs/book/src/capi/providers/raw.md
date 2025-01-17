# Building Raw Images (Baremetal)

## Hypervisor

The image is built using KVM hypervisor.

### Prerequisites for QCOW2

Execute the following command to install qemu-kvm and other packages if you are running Ubuntu 18.04 LTS.

#### Installing packages to use qemu-img

```bash
$ sudo -i
# apt install qemu-kvm libvirt-bin qemu-utils
```

If you're on Ubuntu 20.04 LTS, then execute the following command to install qemu-kvm packages.

```bash
$ sudo -i
# apt install qemu-kvm libvirt-daemon-system libvirt-clients virtinst cpu-checker libguestfs-tools libosinfo-bin
```

#### Adding your user to the kvm group

```bash
$ sudo usermod -a -G kvm <yourusername>
$ sudo chown root:kvm /dev/kvm
```

Then exit and log back in to make the change take place.

## Building Images

The build [prerequisites](../capi.md#prerequisites) for using `image-builder` for
building raw images are managed by running:

```bash
cd image-builder/images/capi
make deps-raw
```

### Building QCOW2 Image

From the `images/capi` directory, run `make build-raw-ubuntu-xxxx`. The image is built and located in images/capi/output/BUILD_NAME+kube-KUBERNETES_VERSION. Please replace xxxx with `2004` or `2004-efi` depending on the version you want to build the image for.

To build a Ubuntu 20.04-based CAPI image, run the following commands -

```bash
$ git clone https://github.com/kubernetes-sigs/image-builder.git
$ cd image-builder/images/capi/
$ make build-qemu-ubuntu-2004
```
