# Overview
Block Storage for VPC offers block-level data storage volumes that can be attached to an instance as either a boot volume or as a data volume. 

## Limitations
The following limits also apply:

 - When you create a new instance, you can create and attach up to four secondary block storage volumes, plus the boot volume.
 - For instances with less than four virtual CPUs, you can attach up to four block storage secondary volumes, plus the boot volume.
 - For instances with four or more virtual CPUs, you can initially create and attach the four secondary volumes, plus the boot volume. You can later attach up to a total of 12 block storage secondary volumes.
 - A total of 750 boot and data block storage volumes per account in a region. You can request an increase of this quota by contacting IBM Support and submitting a support ticket.

Capacity for secondary volumes ranges from 10 to 16,000 GB. 


Capacity

Block Storage for VPC offers a range of storage capacities to meet your requirements. Based on the storage profile. you chose, you can specify 10 - 16,000 GB of capacity per block storage data volume in 1 GB increments. This capacity depends on the block storage IOPS profile you're using. Boot volumes by default are 100 GB. If you provision an instance from a custom image, you can specify boot volume capacity up to 250 GB.
Block storage IOPS profiles

When you provision Block Storage for VPC volumes, you specify an IOPS profile that best meets your storage requirements. Three predefined tiered profiles are available, or you can choose a custom profile. IOPS tiers provide guaranteed IOPS/GB performance for volumes up to 16,000 capacity. A Custom profile defines ranges of volume capacity and IOPS that you can select. These profiles are backed by solid-state drives (SSDs).
How volume bandwidth is allocated

Bandwidth is split between attached block storage volumes and networking. The initial volume and network bandwidth allocation depends on what you set by using the API or by the instance profile you selected.

The maximum volume bandwidth is the highest potential bandwidth that can be allocated to the volume when attached to an instance. In cases where the total maximum bandwidth of attached volumes exceeds the amount available on the instance, the bandwidth for each volume attachment is set proportionally, based on the corresponding volume's maximum bandwidth.

You can reallocate volume and network bandwidth when creating a new instance or for an existing instance. Bandwidth can't be shared between volumes and networking. The instance profile you choose affects total bandwidth. For more information, see Bandwidth allocation for instance profiles.


Bandwidth allocation for volumes attached to an instance

When you provision an instance, bandwidth is allocated between block storage volumes (boot volume and attached block storage volumes)and networking. The maximum bandwidth capacity is determined by the instance profile that you select during instance provisioning. For example, a bx2-2x8 balanced server profile allows a total instance bandwidth of 4,000 Mbps (4 Gbps). The initial storage and network bandwidth allocation depends on what you set by using the API or by the instance profile you selected.

The maximum bandwidth of a volume is the highest potential bandwidth that can be allocated to the volume when attached to an instance. In cases where the total maximum bandwidth of attached volumes exceeds the amount available on the instance, the bandwidth for each volume attachment is set proportionally, based on the corresponding volume's maximum bandwidth.

For example, for the bx2-2x8 profile you might have:

    Volumes: 1,000 Mbps
    Network: 3,000 Mbps

To ensure reasonable boot times, a minimum of 393 Mbps is allocated to the primary boot volume. In the example, the instance's total volume bandwidth is 1,000 Mbps and the remaining 607 Mbps is allocated to any secondary volumes that you attach, up to the maximum bandwidth of the volume. 

https://cloud.ibm.com/docs/vpc?topic=vpc-block-storage-about&interface=ui
https://cloud.ibm.com/docs/vpc?topic=vpc-attaching-block-storage&interface=ui#vol-attach-limits
https://cloud.ibm.com/docs/vpc?topic=vpc-manage-storage-limit&interface=ui
https://cloud.ibm.com/docs/vpc?topic=vpc-expanding-block-storage-volumes
https://cloud.ibm.com/docs/vpc?topic=vpc-adjusting-volume-iops&interface=ui


