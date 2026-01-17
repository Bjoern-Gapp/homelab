# GPU Passthrough (RTX 4070 Ti)

## Goal
Provide near-native GPU performance for a Win11 gaming VM using Proxmox and VFIO.
Use GPU in another VM dedicated to AI-tasks while Win11 VM is down.

## Hardware
- GPU: NVIDIA RTX 4070 Ti
  - VGA: 10de:2782
  - Audio: 10de:22bc

- Mainboard: ASUS TUF B560M-PLUS WIFI

## Steps
1. Enable IOMMU and VT-d in BIOS
2. Bind GPU to vfio-pci on host
3. Attach GPU to Windows VM
4. Install NVIDIA drivers

### Host Preparation

VFIO modules are explicitly loaded at boot to ensure the GPU is claimed
by vfio-pci before any graphics drivers.
