# Process Flow

![Data Upload Process Flow](../../assets/ref/data-lifecycle/upload-process.svg)

This section introduces the data upload process to the CESS network.

When you upload data to CESS, it goes through an erasure coding technology (based on ReedSolomon) and is divided into fixed-size fragments. These fragments are then distributed to storage nodes in the network.

# Summary

To upload data to the CESS network, you must perform the following steps:

1. Purchase storage space
2. Authorize the space usage rights to [**DeOSS**](https://docs.cess.cloud/deoss)
3. Create a bucket (ignore this step if a bucket has already been created)
4. Upload data to DeOSS
5. Check the on-chain data status based on returned transaction hash or download data

For detailed steps, please refer to the [DeOSS guide](https://docs.cess.cloud/deoss).

# Upload Process

The following figure shows the detailed data upload process. The metadata includes the client's calculated data size, hash, segmented list, redundant list, owner's account, data bucket information, etc. The client issues a storage order on-chain, the network allocates storage nodes to store data, and the client obtains the result processed by the network by listening to events. The result contains the storage nodes corresponding to each fragment, and the client needs to store all fragments in these storage nodes:

![Data Upload Flow](../../assets/ref/data-lifecycle/data-upload-flow.svg)

When uploading data, users can choose whether to encrypt the data. If encryption is required, the user must also provide the encryption key. The SDK uses the key entered by the user for encryption, and the SDK does not keep the user key. Users need to keep the key properly. Otherwise, the data cannot be decrypted.

When the user receives the data hash, the data may still need to be stored on the storage node in the CESS network. Only when the data status changes to ACTIVE does the data have been successfully stored.
