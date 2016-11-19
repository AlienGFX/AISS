# AISS
Automated Installer Save Storage

Automated Installer Save Storage (AISS) is a shell script which allows to automatically installing the following produts :
    - A NFS share with nfs-common nfs-kernel-server packages
    - An ISCSI lun with iscsitarget iscsitarget-dkms open-iscsi packages
    - BackUPPC witb backuppc package which saving nfs share to iscsi lun


1) The NFS server must be saved with backupPC
2) BackUPPC must contain all backup of nfs share to own instances iscsi target
3) An instance BackupPC which save NFS data to SRV-NFS which copy to iscsi volume

This script must be executed to backuppc.

With this script, you can :
    - Installing any packages to instances differently
        (nfs-common nfs-kernel-server to SRV-NFS)
        (iscsitarget iscsitarget-dkms open-iscsi to SRV-ISCSI)
        (backuppc to SRV-BACKUP)
    - Configure and Mount ISCSI Lun to SRV-ISCSI
    - Configure and Mount NFS shared to SRV-NFS

AISS.sh can backup to nfs share (srv-nfs) to lun iscsi (srv-iscsi)


              +-----------+        +-----------+
              |           |        |           |
              |           |        |           |
    +---------+  SRV-NFS  |        | SRV-ISCSI <--------+
    |         |           |        |           |        |
    |         |           |        |           |        |
    |         |           |        |           |        |
    |         +-----------+        +-----------+        |
    |                                                   |
    |                                                   |
    |                                                   |
    |                                                   |
    |                  +--------------+                 |
    |                  |              |                 |
    |                  |              |                 |
    |                  |              |                 |
    +------------------>  SRV-BACKUP  +-----------------+
                       |              |
                       |              |
                       |              |
                       +--------------+

