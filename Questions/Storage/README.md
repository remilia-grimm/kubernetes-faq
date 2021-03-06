# Storage 

<details>
<summary>Is a Volume preserved after its Pod's deletion?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">To use a volume, a Pod specifies what volumes to provide for the Pod in the _____ field,&nbsp;</span><span style="color: rgb(34, 34, 34);">and where to mount those into Containers in the&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field.</span></summary>
.spec.volumes
<code>.spec.containers[*].volumeMounts</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary>Can Volumes have hard links to other Volumes?</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using&nbsp;Storage Classes.</span><span style="color: rgb(34, 34, 34);">&nbsp;It is a resource in the cluster just like a node is a cluster resource.&nbsp;</span></summary>
PersistentVolume&nbsp;
<br></details><details>
<summary>A <i>_____&nbsp;</i>is a request for storage by a user.&nbsp;</summary>
PersistentVolumeClaim&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In _____ provisioning, a cluster administrator creates a number of PVs. They carry the details of the real storage, which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption.</span></summary>
static
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A cluster provisioned with many 50Gi PVs. A PVC requests 100Gi. What happens?</span></summary>
<span style="color: rgb(34, 34, 34);">The claim remains unbound.&nbsp;</span><span style="color: rgb(34, 34, 34);">The PVC can be bound when a 100Gi PV is added to the cluster.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If a user deletes a PVC in active use by a Pod, the PVC is...</span></summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">PVC removal is postponed until _____</span></summary>
<span style="color: rgb(34, 34, 34);">the PVC is no longer actively used by any Pods.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">&nbsp;PV removal is postponed until...</span></summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the PV is no longer bound to a PVC.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can see that a PV or a PVC is protected when its status is </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">and the&nbsp;</span><code>Finalizers</code><span style="color: rgb(34, 34, 34);">&nbsp;list includes&nbsp;<font face="monospace">_____</font></span></summary>
<code>Terminating</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><code>kubernetes.io/pvc-protection</code><span style="color: rgb(34, 34, 34);">
</span>
<br></details><details>
<summary>Generally, a PV will have a specific storage capacity. This is set using the PV's <font face="monospace">_____&nbsp;</font>attribute.</summary>
<code>capacity</code>&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can set the value of&nbsp;</span><code>volumeMode</code><span style="color: rgb(34, 34, 34);">&nbsp;to&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">to use a volume as a raw block device. Such volume is presented into a Pod as a block device, without any filesystem on it. This mode is useful to provide a Pod the fastest possible way to access a volume, without any filesystem layer between the Pod and the volume. On the other hand, the application running in the Pod must know how to handle a raw block device.</span></summary>
<code>Block</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">ReadOnlyMany&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted read-only by many nodes</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A volume is said to be _____ when the</span>&nbsp;volume has failed its automatic reclamation.</summary>
Failed
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">PersistentVolumes binds are exclusive, and since PersistentVolumeClaims are namespaced objects, mounting claims with "Many" modes (</span><code>ROX</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>RWX</code><span style="color: rgb(34, 34, 34);">) is only possible within _____</span></summary>
<span style="color: rgb(34, 34, 34);">one namespace</span>
<br></details><details>
<summary>A <font face="monospace">_____&nbsp;</font>is a request for snapshot of a volume by a user. It is similar to a PersistentVolumeClaim.</summary>
<code>VolumeSnapshot</code>&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Are&nbsp;</span><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">,&nbsp;</span><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">, and&nbsp;</span><code>VolumeSnapshotClass</code><span style="color: rgb(34, 34, 34);">&nbsp;part of the core API?&nbsp;</span></summary>
No - they are CustomResourceDefinitions.
<br></details><details>
<summary>In volume snapshots,<font face="monospace"> _____&nbsp;</font><span style="color: rgb(34, 34, 34);">are resources in the cluster.&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">are requests for those resources.&nbsp;</span></summary>
<code>VolumeSnapshotContents</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><code>VolumeSnapshots</code><span style="color: rgb(34, 34, 34);">&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details><details>
<summary>While a snapshot is being taken of a PersistentVolumeClaim, that PersistentVolumeClaim is in-use. If you delete a PersistentVolumeClaim API object in active use as a snapshot source, the PersistentVolumeClaim object is not removed immediately. Instead, removal of the PersistentVolumeClaim object is postponed until the snapshot is _____</summary>
readyToUse or aborted.
<br></details><details>
<summary><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">is the unique identifier of the volume created on the storage backend and returned by the CSI driver during the volume creation. This field is required for dynamically provisioning a snapshot. It specifies the volume source of the snapshot.</span></summary>
<code>volumeHandle</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can provision a new volume, pre-populated with data from a snapshot, by using the </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">field in the&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">&nbsp;object.</span></summary>
<em>dataSource</em><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">PersistentVolumes that are dynamically created by a StorageClass will have the reclaim policy specified in the&nbsp;</span><code>reclaimPolicy</code><span style="color: rgb(34, 34, 34);">&nbsp;field of the class, which can be...</span></summary>
<span style="color: rgb(34, 34, 34);">&nbsp;</span><code>Delete</code><span style="color: rgb(34, 34, 34);">&nbsp;or&nbsp;</span><code>Retain</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">To enable dynamic volume provisioning, a cluster administrator needs to pre-create one or more _____ objects for users.</span></summary>
<span style="color: rgb(34, 34, 34);">StorageClass</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a Container crashes, kubelet will restart it, but its on-disk files will be...&nbsp;</span></summary>
Lost, unless stored on a Volume
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If a PV was dynamically provisioned for a new PVC, the loop will always _____ that PV to the PVC.</span></summary>
binds
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A Pod uses a PersistentVolume. This PV has a node affinity towards certain nodes. Where will the Pod be scheduled?</span></summary>
To the node where the PV is available from.
<br></details><details>
<summary>A volume is said to be _____ when it is free and not yet bound to a claim.</summary>
Available
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When running Containers together in a&nbsp;</span><code>Pod</code><span style="color: rgb(34, 34, 34);">&nbsp;it is often necessary to share files between those Containers. The Kubernetes&nbsp;_____&nbsp;</span><span style="color: rgb(34, 34, 34);">abstraction solves this problem.</span></summary>
Volume&nbsp;
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Is a volume just a directory with data, accessible to the Containers in its enclosing Pod?</span></summary>
Yes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Can Volumes mount into other volumes?</span></summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A control loop in the master watches for new PVCs, finds a matching PV (if possible), and _____ them.&nbsp;</span></summary>
binds
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">You can only expand a PVC if its storage class's </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">field is set to true.&nbsp;</span>To request a larger volume for a PVC, edit the PVC object and specify a larger size. This triggers expansion of the volume that backs the underlying PersistentVolume. A new PersistentVolume is never created to satisfy the claim. Instead, an existing volume is resized.</summary>
<code>allowVolumeExpansion</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary>Can you resize an in-use PVC?</summary>
Yes - since Kubernetes 1.15.&nbsp;<span style="color: rgb(136, 136, 136);">The&nbsp;</span><code>ExpandInUsePersistentVolumes</code>&nbsp;feature must be enabled.
<br></details><details>
<summary>Kubernetes supports two&nbsp;<code>volumeModes</code>&nbsp;of PersistentVolumes:&nbsp;</summary>
<code>Filesystem</code>&nbsp;and&nbsp;<code>Block</code>.
<br></details><details>
<summary><code>volumeMode</code>&nbsp;is an optional API parameter.&nbsp;<font face="monospace">_____&nbsp;</font>is the default mode used when&nbsp;<code>volumeMode</code>&nbsp;parameter is omitted.</summary>
<code>Filesystem</code>&nbsp;
<br></details><details>
<summary>A volume with <font face="monospace">_____</font>&nbsp;is&nbsp;<em>mounted</em>&nbsp;into Pods into a directory. If the volume is backed by a block device and the device is empty, Kuberneretes creates a filesystem on the device before mounting it for the first time.</summary>
volumeMode: Filesystem
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">ReadWriteMany&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">&nbsp;the volume can be mounted as read-write by many nodes</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A PV can have a class, which is specified by setting the </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">attribute to the name of a&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/storage-classes/">StorageClass</a><span style="color: rgb(34, 34, 34);">.&nbsp;</span></summary>
<code>storageClassName</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A claim can request a particular class by specifying the name of a StorageClass</span><span style="color: rgb(34, 34, 34);">&nbsp;using the attribute&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">.&nbsp;</span></summary>
storageClassName
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Similar to how API resources&nbsp;</span><code>PersistentVolume</code><span style="color: rgb(34, 34, 34);">&nbsp;and&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">&nbsp;are used to provision volumes for users and administrators,&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">and&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">API resources are provided to create volume snapshots for users and administrators.</span></summary>
VolumeSnapshot&nbsp;<code>
</code><code>VolumeSnapshotContent</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">&nbsp;support is only available for _____ drivers.</span></summary>
<span style="color: rgb(34, 34, 34);">CSI&nbsp;</span>
<br></details><details>
<summary>The CRDs and snapshot controller installations are the responsibility of _____</summary>
the Kubernetes distribution
<br></details><details>
<summary>The snapshot controller handles the binding of a&nbsp;<code>VolumeSnapshot</code>&nbsp;object with an appropriate&nbsp;<code>VolumeSnapshotContent</code>&nbsp;object, in both pre-provisioned and dynamically provisioned scenarios. The binding is a _____ mapping.&nbsp;
In the case of pre-provisioned binding, the VolumeSnapshot will remain unbound until the requested VolumeSnapshotContent object is created.</summary>
one-to-one
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">An administrator can mark a specific&nbsp;</span><code>StorageClass</code><span style="color: rgb(34, 34, 34);">&nbsp;as default by adding the&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">&nbsp;annotation to it.</span></summary>
storageclass.kubernetes.io/is-default-class
<br></details><details>
<summary>Can you attach as many volumes as you want to a node?</summary>
No - depends on the cloud provider's permitted limit.
<br></details><details>
<summary>A PVC to PV binding is a one-to-one mapping, using a <b>_____&nbsp;</b>which is a bi-directional binding between the PersistentVolume and the PersistentVolumeClaim.&nbsp;</summary>
ClaimRef
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A PV of a particular class can only be bound to PVCs requesting that class. A PV with no&nbsp;</span>_____&nbsp;<span style="color: rgb(34, 34, 34);">has no class and can only be bound to PVCs that request no particular class.</span></summary>
storageClassName
<br></details><details>
<summary>A volume is called _____ when it is bound to a claim.</summary>
Bound
<br></details><details>
<summary>A volume is said to be _____, when the claim has been deleted, but the resource is not yet reclaim by the cluster.</summary>
Released
<br></details><details>
<summary>Mounted directories that are accessible from inside containers.</summary>
Volumes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A Kubernetes volume has an explicit lifetime - the same as _____</span></summary>
The Pod that encloses it
<br></details><details>
<summary>Is a Volume preserved across Container restarts?</summary>
Yes
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Managing storage is a distinct problem from managing compute instances. The PersistentVolume subsystem provides an API for users and administrators that abstracts details of how storage is provided from how it is consumed. To do this, we introduce two new API resources: _____ and _____.</span></summary>
<span style="color: rgb(34, 34, 34);">PersistentVolume&nbsp;</span><span style="color: rgb(34, 34, 34);">
</span><span style="color: rgb(34, 34, 34);">PersistentVolumeClaim</span><span style="color: rgb(34, 34, 34);">
</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Do PersistentVolumes have a lifecycle dependent on the Pods that use the PV?</span></summary>
No
<br></details><details>
<summary>There are two ways PVs may be provisioned:</summary>
statically or dynamically.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When none of the static PVs the administrator created match a user's PersistentVolumeClaim, the cluster may try to _____ provision a volume specially for the PVC. This provisioning is based on StorageClasses: the PVC must request a storage class</span><span style="color: rgb(34, 34, 34);">&nbsp;and the administrator must have created and configured that class for dynamic provisioning to occur.</span></summary>
<span style="color: rgb(34, 34, 34);">dynamically</span>
<br></details><details>
<summary>Once bound, PersistentVolumeClaim binds are _____, regardless of how they were bound.&nbsp;</summary>
exclusive
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Once a user has a claim and that claim is bound, the bound PV belongs to the user for as long as they need it. Users schedule Pods and access their claimed PVs by including a </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">section in a Pod's&nbsp;</span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">block.</span></summary>
<code>persistentVolumeClaim</code><code>
</code><code><code>volumes</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">If an admin deletes a PV that is bound to a PVC, the PV is...</span></summary>
<span style="color: rgb(34, 34, 34);">not removed immediately.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">When a user is done with their volume, they can delete the PVC objects from the API that allows reclamation of the resource. The reclaim policy for a PersistentVolume tells the cluster what to do with the volume after it has been released of its claim. Currently, volumes can either be _____, _____, _____.</span></summary>
<span style="color: rgb(34, 34, 34);">Retained, Recycled, Deleted.</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">The </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">reclaim policy allows for manual reclamation of the resource. When the PersistentVolumeClaim is deleted, the PersistentVolume still exists and the volume is considered "released". But it is not yet available for another claim because the previous claimant's data remains on the volume.</span></summary>
<code>Retain</code>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">For volume plugins that support the </span><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">reclaim policy, deletion removes both the PersistentVolume object from Kubernetes, as well as the associated storage asset in the external cloud infrastructure. Volumes that were dynamically provisioned inherit the&nbsp;</span><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy">reclaim policy of their StorageClass</a><span style="color: rgb(34, 34, 34);">, which defaults to&nbsp;</span><font face="monospace">_____</font><span style="color: rgb(34, 34, 34);">. The administrator should configure the StorageClass according to users' expectations; otherwise, the PV must be edited or patched after it is created.</span></summary>
<code>Delete</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">ReadWriteOnce&nbsp;</span></summary>
<span style="color: rgb(34, 34, 34);">the volume can be mounted as read-write by a single node</span>
<br></details><details>
<summary>Can a volume be mounted using several access modes at a time?&nbsp;</summary>
No
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A PV can specify _____</span><span style="color: rgb(34, 34, 34);">&nbsp;to define constraints that limit what nodes this volume can be accessed from.&nbsp;</span></summary>
node affinity
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">In Kubernetes, a </span><i>_____&nbsp;</i><span style="color: rgb(34, 34, 34);">represents a snapshot of a volume on a storage system.</span></summary>
<em>VolumeSnapshot</em>
<br></details><details>
<summary>A <font face="monospace">_____&nbsp;</font>is a snapshot taken from a volume in the cluster that has been provisioned by an administrator. It is a resource in the cluster just like a PersistentVolume is a cluster resource.</summary>
<code>VolumeSnapshotContent</code>&nbsp;
<br></details><details>
<summary><font face="monospace">_____&nbsp;</font><span style="color: rgb(34, 34, 34);">allows you to specify different attributes belonging to a&nbsp;</span><code>VolumeSnapshot</code><span style="color: rgb(34, 34, 34);">. These attributes may differ among snapshots taken from the same volume on the storage system and therefore cannot be expressed by using the same&nbsp;</span><code>StorageClass</code><span style="color: rgb(34, 34, 34);">&nbsp;of a&nbsp;</span><code>PersistentVolumeClaim</code><span style="color: rgb(34, 34, 34);">.</span></summary>
<code>VolumeSnapshotClass</code><span style="color: rgb(34, 34, 34);">&nbsp;</span>
<br></details><details>
<summary>There are two ways snapshots may be provisioned:&nbsp;</summary>
pre-provisioned or dynamically provisioned.
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">A cluster administrator creates a number of&nbsp;</span><code>VolumeSnapshotContents</code><span style="color: rgb(34, 34, 34);">. They carry the details of the real volume snapshot on the storage system which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption. This is the description of _____ snapshot provisioning.</span></summary>
pre-provisioned
<br></details><details>
<summary>Instead of using a pre-existing snapshot, you can request that a snapshot to be _____ taken from a PersistentVolumeClaim. The&nbsp;<a href="https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/">VolumeSnapshotClass</a>&nbsp;specifies storage provider-specific parameters to use when taking a snapshot.</summary>
dynamically
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Users request dynamically provisioned storage by including a _____ in their&nbsp;</span><code>PersistentVolumeClaim</code></summary>
<span style="color: rgb(34, 34, 34);">.spec.storageClassName</span>
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Claims will remain _____ indefinitely if a matching volume does not exist, and will be bound as matching volumes become available.&nbsp;</span></summary>
unbound
<br></details><details>
<summary><span style="color: rgb(34, 34, 34);">Only PVs of the requested class, ones with the same&nbsp;</span>_____&nbsp;<span style="color: rgb(34, 34, 34);">as the PVC, can be bound to the PVC.</span></summary>
StorageClassName
<br></details>