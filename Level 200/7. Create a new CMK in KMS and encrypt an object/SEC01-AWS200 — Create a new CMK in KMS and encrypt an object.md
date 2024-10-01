# SEC01-AWS200 — Create a new CMK in KMS and encrypt an object

## Cloud Service Provider
- Amazon Web Services

## Difficulty

- Level 200 (Intermediate)

## Project's Author(s)

- [Andrew Brown](https://twitter.com/andrewbrown)

## Objectives

### You need to complete the following:

- Create a new Customer Master Key (CMK) in Key Management Service (KMS)
- Create a new S3 bucket
- Upload an object (file) to the S3 Bucket
- Encrypt the uploaded file with your custom CMK

### You need to answer the following:

## What is a Hardware Security Module (HSM)?

A **Hardware Security Module (HSM)** is a physical device designed to manage and protect cryptographic keys and perform encryption and decryption operations. HSMs provide a high level of security by ensuring that keys are stored in a tamper-resistant environment and by performing cryptographic operations in a secure manner. They are commonly used to safeguard sensitive data and comply with security standards and regulations.

## What is the Difference Between Multi-Tenant and Single-Tenant HSM?

- **Multi-Tenant HSM**: In a multi-tenant HSM environment, a single HSM device or instance is shared among multiple customers or tenants. Each tenant’s data and keys are logically separated, but they share the same physical hardware. This setup is typically more cost-effective but may offer less isolation and control compared to single-tenant setups.

- **Single-Tenant HSM**: In a single-tenant HSM environment, the HSM device or instance is dedicated to a single customer or tenant. This means that the entire hardware and its resources are exclusively used by that customer, providing higher isolation, control, and potentially better security. Single-tenant HSMs usually come at a higher cost due to their exclusivity.

## What is the Cost for CloudHSM?

As of the latest pricing information, **AWS CloudHSM** charges based on the number of HSM instances and the amount of data processed. The pricing includes:
- **Hourly Charges**: For each HSM instance.
- **Data Transfer Charges**: For data transferred out of the HSM.

Please refer to the [AWS CloudHSM Pricing page](https://aws.amazon.com/cloudhsm/pricing/) for the most current and detailed pricing information.

## What is Key Rotation?

**Key Rotation** refers to the practice of periodically changing cryptographic keys used for encrypting and decrypting data. Regularly rotating keys helps enhance security by limiting the potential impact of a key compromise. Key rotation ensures that even if a key is exposed, its exposure is limited to a shorter period, reducing the risk of unauthorized access to encrypted data.

## How Much Do KMS Keys Cost?

**AWS Key Management Service (KMS)** pricing generally involves:
- **Key Usage Charges**: Costs associated with the number of requests made to the KMS service, such as encryption and decryption operations.
- **Key Management Charges**: Costs associated with the creation and storage of keys. 

As of the latest information, pricing details are:
- **AWS KMS Keys**: Typically, there is no charge for the first 100,000 requests per month for each key. Beyond this, there are additional charges based on the number of requests.
- **Custom Key Store**: Charges for custom key stores include additional costs for the use of hardware security modules (HSMs).

For the latest and most detailed pricing information, please refer to the [AWS KMS Pricing page](https://aws.amazon.com/kms/pricing/).

## Ideas

- Creating a single CMK key will result in $1 USD per month so ensure
  you delete your key at the end of this project.

## References

- [Key Management Service](https://aws.amazon.com/kms/)
- [CloudHSM](https://aws.amazon.com/cloudhsm/)
- [AWS Key Management Service concepts](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)

## Output
![{353F0602-3F6F-433C-AED0-564B1F24C184}](https://github.com/shubhammurti/AWS-Projects-Portfolio/blob/d041eddb576ed88d906f59eacc6359442a45beb1/Level%20200/7.%20Create%20a%20new%20CMK%20in%20KMS%20and%20encrypt%20an%20object/Image.png)
