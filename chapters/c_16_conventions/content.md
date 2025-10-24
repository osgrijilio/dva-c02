# Conventions and Processes

My conventions.

## Naming conventions

Name things and tag'em.

Bucket names are global. There might be collisions or unintended usage from third parties.  Dots only make sense for buckets that hold statics sites.

Use this name format: __*X(7)-Y(10)-TYPE\[-CUST-GUID]*__

where:

- __*XXXXXXX*__ application name. might be less digits, but no more than 7.

- __*YYYYYYYYYY*__ is a subname partition/sequence/concept, as you would use it in the tag.
   might be less digits, but no more than 10.

- __*TYPE*__ is a type, like acl or sg. No more than 5 letters.

- __*-CUST*__ is an optional customer id. No more than 5 letters.

  Omit both CUST and GUID, or provide both at the same time.

- __*-GUID*__ is an optional globally unique identifier(GUID). For example:

  ```bash
   uuidgen | tr -d - | tr '[:upper:]' '[:lower:]'
   e901ee44118c4e9e82b8360966d414d0
   ```

Examples:

```text
demo1-1-acl
demo1-2-acl
demo1-public-sg
demo1-1-key
demo2-11-acl
demo1-photos-s3-iisa-e901ee44118c4e9e82b8360966d414d0
demo1-resumes-s3-iisa-36e862ab030a492982798cdebc8024cb
```

At all times we use DNS compatible names. No spaces, no underscores.

This convention __*X(7)-Y(10)-TYPE\[-CUST-GUID]*__ can be seen as __*private-public*__

where

- __*private*__ is the part __*X(7)-Y(10)-TYPE*__, and

- __*public*__ is the optional part __*-CUST-GUID*__
  
In most names, the private part is enough to identify a resource, but in globally exposed names, the public part is required.

## General purpose buckets naming conventions

The following naming rules apply for general purpose buckets.

- Bucket names must be between 3 (min) and 63 (max) characters long.
- Bucket names can consist only of lowercase letters, numbers, periods (.), and hyphens (-).
- Bucket names must begin and end with a letter or number.
- Bucket names must not contain two adjacent periods.
- Bucket names must not be formatted as an IP address (for example, 192.168.5.4).
- Bucket names must not start with the prefix xn--.
- Bucket names must not start with the prefix sthree-.
- Bucket names must not start with the prefix amzn-s3-demo-.
- Bucket names must not end with the suffix -s3alias. This suffix is reserved for access point alias names. For more information, see Access point aliases.
- Bucket names must not end with the suffix --ol-s3. This suffix is reserved for Object Lambda Access Point alias names. For more information, see How to use a bucket-style alias for your S3 bucket Object Lambda Access Point.
- Bucket names must not end with the suffix .mrap. This suffix is reserved for Multi-Region Access Point names. For more information, see Rules for naming Amazon S3 Multi-Region Access Points.
- Bucket names must not end with the suffix --x-s3. This suffix is reserved for directory buckets. For more information, see Directory bucket naming rules.
- Bucket names must not end with the suffix --table-s3. This suffix is reserved for S3 Tables buckets. For more information, see Amazon S3 table bucket, table, and namespace naming rules.
- Buckets used with Amazon S3 Transfer Acceleration can't have periods (.) in their names. For more information about Transfer Acceleration, see Configuring fast, secure file transfers using Amazon S3 Transfer Acceleration.

Important

- Bucket names must be unique across all AWS accounts in all of the AWS Regions within a partition. A partition is a grouping of Regions. AWS currently has three partitions: aws (commercial Regions), aws-cn (China Regions), and aws-us-gov (AWS GovCloud (US) Regions).
- A bucket name can't be used by another AWS account in the same partition until the bucket is deleted. After you delete a bucket, be aware that another AWS account in the same partition can use the same bucket name for a new bucket and can therefore potentially receive requests intended for the deleted bucket. If you want to prevent this, or if you want to continue to use the same bucket name, don't delete the bucket. We recommend that you empty the bucket and keep it, and instead, block any bucket requests as needed. For buckets no longer in active use, we recommend emptying the bucket of all objects to minimize costs while retaining the bucket itself.
- When you create a general purpose bucket, you choose its name and the AWS Region to create it in. After you create a general purpose bucket, you can't change its name or Region.
- Don't include sensitive information in the bucket name. The bucket name is visible in the URLs that point to the objects in the bucket.

### Best practices

When naming your general purpose buckets, consider the following bucket naming best practices.

- __Choose a bucket naming scheme that's unlikely to cause naming conflicts__

  If your application automatically creates buckets, choose a bucket naming scheme that's unlikely to cause naming conflicts. Ensure that your application logic will choose a different bucket name if a bucket name is already taken.

- __Append globally unique identifiers (GUIDs) to bucket names__

  We recommend that you create bucket names that aren't predictable. Don't write code assuming your chosen bucket name is available unless you have already created the bucket. One method for creating bucket names that aren't predictable is to append a Globally Unique Identifier (GUID) to your bucket name, for example, amzn-s3-demo-bucket-a1b2c3d4-5678-90ab-cdef-example11111. For more information, see Creating a bucket that uses a GUID in the bucket name.

- __Avoid using periods (.) in bucket names__

  For best compatibility, we recommend that you avoid using periods (.) in bucket names, except for buckets that are used only for static website hosting. If you include periods in a bucket's name, you can't use virtual-host-style addressing over HTTPS, unless you perform your own certificate validation. The security certificates used for virtual hosting of buckets don't work for buckets with periods in their names.

  This limitation doesn't affect buckets used for static website hosting, because static website hosting is available only over HTTP. For more information about virtual-host-style addressing, see Virtual hosting of general purpose buckets. For more information about static website hosting, see Hosting a static website using Amazon S3.

- __Choose a relevant name__

  When you name a bucket, we recommend that you choose a name that's relevant to you or your business. Avoid using names associated with others. For example, avoid using AWS or Amazon in your bucket name.

- __Don't delete buckets so that you can reuse bucket names__

  If a bucket is empty, you can delete it. After a bucket is deleted, the name becomes available for reuse. However, you aren't guaranteed to be able to reuse the name right away, or at all. After you delete a bucket, some time might pass before you can reuse the name. In addition, another AWS account might create a bucket with the same name before you can reuse the name.

  After you delete a general purpose bucket, be aware that another AWS account in the same partition can use the same bucket name for a new bucket and can therefore potentially receive requests intended for the deleted general purpose bucket. If you want to prevent this, or if you want to continue to use the same general purpose bucket name, don't delete the general purpose bucket. We recommend that you empty the bucket and keep it, and instead, block any bucket requests as needed.

## Tags

Recommendeg tags:

- app-name: x(7). For example, demo01.

- app-function: X(10). A concept inside your application

- budget-id: X(10). An identifier for budgeting.

- env-type:
  - dev
  - sit
  - crp
  - uat
  - prd

## Test processes and Environment types

Some clients might do with less than 5 enviroments, so we will adjust to their practice.

|Feature | System Integration Testing (SIT) | Conference Room Pilot (CRP) | User Acceptance Testing (UAT)
|-|-|-|-
|Primary Goal | Verify that integrated system components work together according to technical specifications. | Validate and refine end-to-end business processes in a controlled environment. | Obtain final user sign-off by confirming the system meets business requirements and is ready for real-world use.
|When it Occurs | After unit testing is completed and all system components are integrated. | Early in the implementation during the design or build phase, with multiple sessions possible. | After all modifications and bug fixes from previous testing are addressed, just before go-live.
|Who Performs It | Development and QA teams. | Key stakeholders and subject matter experts from the business. | End-users and business process owners.
|Pace and Focus | Methodical testing focused on technical integrity, data flow, and control flow. | Slower and more collaborative, focusing on the end-to-end business process flow. | Faster-paced, with a broader group of users validating the overall business flow.
|Environment Used | Dedicated testing environment. | Staging environment, to be as close to the final system as possible. | Staging environment, replicating the production environment.
|Data Used | Test data created by the development or testing team. | A sample of client data. | The full, production-like client dataset.
|What's Found | Integration issues between modules, data flow errors, and other technical problems. | Missing functional requirements, process inefficiencies, and design flaws. | Last-minute, high-priority "gotchas" or show-stopper bugs.
|Outcome | Approval to move to the next phase, often user acceptance testing. | Refined business processes and a stable configuration for UAT. | A final go/no-go decision and sign-off for deployment to production.
