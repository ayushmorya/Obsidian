Creating and mounting a new file system in Linux involves several steps, from partitioning the disk to mounting it for use. Here’s a step-by-step guide:

---

## **1. Identify Available Disks**

First, check available disks and partitions using:

```bash
lsblk
```

or

```bash
fdisk -l
```

This will list all disks (e.g., `/dev/sdb`, `/dev/sdc`).

---

## **2. Create a New Partition (if needed)**

If the disk is new, you need to partition it.

### **Using `fdisk`**

1. Open the disk partition tool:
    
    ```bash
    sudo fdisk /dev/sdb
    ```
    
2. Create a new partition:
    - Press `n` (new partition).
    - Choose `p` (primary).
    - Select partition number (default: 1).
    - Define the size (or press Enter to use full disk).
3. Save changes:
    - Press `w` (write changes).

### **Using `parted` (for GPT disks)**

For larger disks:

```bash
sudo parted /dev/sdb mklabel gpt
sudo parted /dev/sdb mkpart primary ext4 0% 100%
```

---

## **3. Format the Partition with a File System**

Once the partition is created (e.g., `/dev/sdb1`), format it with a file system:

For **EXT4** (commonly used):

```bash
sudo mkfs.ext4 /dev/sdb1
```

For **XFS** (for high-performance needs):

```bash
sudo mkfs.xfs /dev/sdb1
```

---

## **4. Create a Mount Point**

A mount point is a directory where the file system will be attached.

Example:

```bash
sudo mkdir /mnt/newdisk
```

---

## **5. Mount the File System**

To mount the new file system manually:

```bash
sudo mount /dev/sdb1 /mnt/newdisk
```

Check if it's mounted:

```bash
df -h
```

---

## **6. Make the Mount Persistent (Auto-Mount on Boot)**

By default, the mount disappears after a reboot. To make it permanent:

1. Get the **UUID** of the partition:
    
    ```bash
    blkid /dev/sdb1
    ```
    
2. Add an entry to `/etc/fstab`:
    
    ```bash
    sudo nano /etc/fstab
    ```
    
    Add this line:
    
    ```
    UUID=your-uuid-here  /mnt/newdisk  ext4  defaults  0  2
    ```
    
3. Save and exit (`Ctrl+X`, `Y`, `Enter`).
4. Reload fstab:
    
    ```bash
    sudo mount -a
    ```
    

---

### **7. Verify Everything**

- Check if mounted:
    
    ```bash
    df -h
    ```
    
- Test writing files:
    
    ```bash
    sudo touch /mnt/newdisk/testfile
    ```
    

Now, your new file system is ready to use! 🚀