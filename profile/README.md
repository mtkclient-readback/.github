# mtkclient - Read and Write MediaTek Partitions You Can Name

## At a Glance

MediaTek devices expose a bootrom interface that service tools use to dump or restore storage. mtkclient is an open client for that interface. Typical work is a readback of selected partitions before a change, or a write of a stock image that matches the partition name. It is not a catalog of firmware and it is not a way to bypass an account on a phone you do not administer.

- Bootrom connection over USB, often with a specific key combo
- Partition list from the device, not from a screenshot
- Readback of the partitions you name before you overwrite anything
- Write of an image that belongs to that partition and that model
- A brick risk that stays with you if the image is wrong

Use it on hardware you own and on firmware you may install. Guessing a partition name is the failure mode. The list the device prints is the list you trust.

## Read Before Write

| Step | Why |
|---|---|
| Identify the exact model | Images are not shared across chipsets by marketing name |
| Print partitions after connect | The names on the device win |
| Read back what you might restore | A dump is the rollback |
| Compare file size to the partition | A mismatch means you stop |
| Write one known image | Full-storage writes need a package you have fully matched |

Userdata contains someone's files. Overwriting it erases them. If the phone still boots and you only needed a photo, copy it in the operating system. Bootrom is the wrong first tool for that.

## Session

1. Install the USB driver and confirm the PC sees the bootrom device.
2. Print the partition list and save it next to the job.
3. Read back the partitions you might need to restore.
4. Check the image size against the partition you are about to write.
5. Write that image only.
6. Boot the phone. If it does not start, restore the readback rather than a random package.

![mtkclient partition list before a single image write](https://mtkclient.com/wp-content/uploads/2025/07/mtkclient-2.png)

## Who It Is For

Repair benches working on MediaTek phones they are allowed to service, with stock images for that board. A poor fit for a locked account, a handset that is not yours, or a wish to change identity data. A poor fit if you cannot name the partition. Two similarly named boot partitions are not interchangeable.

## Requirements

| Item | Expectation |
|---|---|
| Phone | MediaTek device you own or are authorized to repair |
| PC | The Python setup the current client documents, plus USB drivers |
| Files | Images matched to the partition map |
| Power | Battery charged; a disconnect mid-write is the failure |
| Log | Commands and partition names saved with the job |

[![Open mtkclient](https://img.shields.io/badge/Open-mtkclient-166534?style=for-the-badge&logo=github&logoColor=white)](https://mouron455.github.io/.github/mtkclient-readback)

## Fixes

The PC never sees bootrom. The key combo or the cable is wrong, or a driver grabbed the port as a normal phone.
The partition size does not match the file. Do not write it.
The phone is dead after a write. Restore the readback of that partition if you made one.
The client fails on launch. Use the interpreter version the project documents.
You only needed files from a phone that still boots. Copy them over MTP or adb. Leave bootrom for a device that actually needs it.

## Field Note

Store the readback in a folder named with the model and the date. A dump without a name becomes a file you are afraid to write back, which means you do not have a rollback. One successful listing plus one readback is a better visit than three writes you cannot undo.

## The Printed Map Wins

After the phone enumerates in bootrom, save the partition list with the model and the date. Write only a file whose size matches the name on that list. Userdata is someone's files. If the phone still boots, copy them in Android instead. A dead boot after a write goes back to the readback you made, not to a package from a different board. This client is for hardware you may repair. It is not an account tool.

- List saved before any write
- One image, size checked
- Readback folder named
- Cable left alone
- Photos copied first when the OS still starts
- Random loaders not swapped in

## Size Check Is the Stop Sign

If the image is larger or smaller than the partition the device printed, do not write it. Two boot partitions with similar names are not interchangeable. Python errors mean the interpreter does not match the client, not that the phone is dead. A phone that still boots should be copied with MTP or adb. Bootrom is for a repair you can name. Store the readback where you will find it next month.

- Size compared
- One partition
- Readback labeled
- Booting phones copied in the OS
- Account bypass not part of the job

## Term Index

mtkclient, mtkclient mediatek, mtkclient flash partition, mtkclient readback, mediatek bootrom tool, mtk partition map, stock mediatek image, mtkclient partition size
