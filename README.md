# Using Resource-Based Policies to Secure an S3 Bucket

## Overview
In this lab, you will configure permissions using AWS Identity and Access Management (IAM) identity-based and resource-based policies, including Amazon S3 bucket policies. You will learn how these policies define access permissions and how an IAM user can assume a role to gain different access.

## Objectives
By the end of this lab, you should be able to:
- Use IAM identity-based and resource-based policies for fine-grained access control.
- Describe how an IAM user can assume an IAM role to gain different permissions.
- Explain how S3 bucket policies and IAM policies affect user access across AWS services.

<img width="787" alt="Screenshot 2024-11-02 at 7 07 28 PM" src="https://github.com/user-attachments/assets/f7993421-f972-4a0a-aa15-74616eb500c7">

By the end of this lab, you will have created the architecture shown in the following diagram.

<img width="831" alt="Screenshot 2024-11-02 at 7 08 06 PM" src="https://github.com/user-attachments/assets/0ce6e7ee-75f8-40e3-8351-6accd49a8c5a">

## Steps

### Task 1: Log in as IAM User
1. Log in as the IAM user `devuser` using the IAMUserLoginURL and provided credentials.
2. Ensure you do not change the AWS region during this lab.

### Task 2: Attempting Read-Level Access
1. **Access EC2 Console:**
   - Navigate to **Services > Compute > EC2**.
   - Attempt to perform actions like launching instances (you will see authorization errors).
   
2. **Access S3 Console:**
   - Navigate to **Services > Storage > S3**.
   - Notice that the access column shows "Insufficient permissions" for all buckets.

### Task 3: Analyzing Identity-Based Policy
1. Access the IAM console.
2. View the `DeveloperGroup` that `devuser` is part of.
3. Review the `DeveloperGroupPolicy` attached to this group.
4. Save the policy details as `DeveloperGroupPolicy.json`.

### Task 4: Attempting Write-Level Access
1. **Create an S3 Bucket:**
   - In S3, create a new bucket with your initials and a random number.
   
2. **Upload an Object:**
   - Attempt to upload the `DeveloperGroupPolicy.json` file to the new bucket (you will receive an access denied message).
   
3. Analyze the policy to understand why you could create a bucket but not upload an object.

### Task 5: Assuming an IAM Role
1. Attempt to access `bucket1` and `bucket2` to download objects (you will receive access denied errors).
2. **Assume the `BucketsAccessRole`:**
   - Switch roles to `BucketsAccessRole`.
   - Download an object from `bucket1` successfully.

<img width="733" alt="Screenshot 2024-11-02 at 7 08 59 PM" src="https://github.com/user-attachments/assets/db079ae5-dcb0-4a82-9ae9-8b1b0835c602">

3. Attempt to upload an object to `bucket2` and analyze the permissions granted by the role.

<img width="743" alt="Screenshot 2024-11-02 at 7 09 52 PM" src="https://github.com/user-attachments/assets/badfc928-c847-4dda-b8da-8a8eeab00dfe">

### Task 6: Understanding Resource-Based Policies
1. Review the bucket policy associated with `bucket2`:
   - Understand how resource-based policies work in conjunction with role-based policies.
   
### Challenge Task
1. Attempt to upload the `Image2.jpg` file to `bucket3` as `devuser` (you will fail).
2. Switch to `BucketsAccessRole` and attempt the same actions to investigate permissions.

---

## Conclusion
By following these tasks, you have gained practical experience in configuring and analyzing IAM and S3 bucket policies, understanding how roles and policies interact to control access to AWS resources.
