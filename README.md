<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>


# Cloud Security with AWS IAM

**Project Link:** [View Project](https://nextwork.ai/projects/51a5fd24-7458-58a6-8653-9b90119a0e4a)

**Author:** Stuart

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use Amazon Web Services (AWS) Identity and Access Management (IAM) to manage user authentication and authorization within an AWS account. This includes controlling who can access AWS resources and defining the permissions assigned to users and groups. The purpose of this project is to gain hands-on experience with IAM, strengthen my understanding of access management, and learn how IAM plays a critical role in securing AWS environments.

### Tools and concepts

Services I used were EC2 instances, IAM user groups, users, and policies. Key concepts I learned include creating user groups and users with limited access using JSON policies. I also learned how to create an account alias to make it easier for users to access and how to test policies without disrupting operations.

### Project reflection

This project took me approximately 45 minutes to complete. The most challenging part was the policies. It was most rewarding to test and see the policies worked and denied access to an important instance.


## Tags

### What I did in this step

In this step, I will launch two Amazon EC2 instances to increase NextWork's computing capacity in preparation for the upcoming holiday season. With the expected increase in website traffic, these additional instances will provide the computing resources needed to handle higher workloads and maintain reliable performance.

### Understanding tags

Tags in AWS are used to organize, identify, and manage resources such as EC2 instances. They consist of key-value pairs that make it easier to locate and differentiate resources based on their purpose or environment. For example, tags can help distinguish between production and development instances, making resource management more efficient as an AWS environment grows.

### My tag configuration

The tag I’ve used on my EC2 instances is called development and production. The value I’ve assigned for my instances are Env

![Tags](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_2e0e5a5d)

## IAM Policies

### What I did in this step

In this step, I will create an AWS IAM policy that grants our new intern access to the development EC2 instance while restricting access to the production instance. This ensures the intern can safely test and make changes in the development environment without affecting production resources. By implementing this policy, I will demonstrate how IAM can be used to manage permissions and enforce the principle of least privilege within an AWS environment.

### Understanding IAM policies

AWS IAM policies are used to define and control permissions for accessing AWS resources. They specify which actions users, groups, or roles are allowed or denied permission to perform on specific resources. IAM policies help improve security by ensuring users only have access to the resources and actions necessary for their responsibilities, following the principle of least privilege.

### The policy I set up

For this project, I’ve set up a policy using JSON

### Policy effect

I’ve created a policy that allows access and actions to instances with the tag development but also denies the creation and deletion of tags.

### Understanding Effect, Action, and Resource

In an AWS IAM JSON policy, Effect, Action, and Resource are used to control permissions. Effect determines whether an action is allowed or denied, while Action defines what a user can or cannot do, such as starting or stopping an EC2 instance. Resource specifies which AWS resources those permissions apply to. These three elements work together to make sure users only have access to what they need.

## My JSON Policy

![My JSON Policy](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1c864649)

## Account Alias

### What I did in this step

In this step, I will simplify user login to my AWS account using an account alias because our intern needs access.

### Understanding account aliases

An AWS account alias replaces your account ID in the IAM user sign-in URL with a custom name, making the link easier for users to remember and access when signing in to AWS.

### Setting up my account alias

Creating an account alias took me a minute. Now, my new AWS console sign-in URL is https://nextwork-alias-stuartdiperna.signin.aws.amazon.com/console

![Account Alias](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0eb4439b)

## IAM Users and User Groups

### What I did in this step

In this step, I will set up a dedicated IAM group for all NextWork interns, so I can manage all interns' permissions from one place and set up dedicated IAM user so the interns have a way to log in because we do not want to give interns access to my account so we need to set up a user account for the intern to log into and groups to easily manage the user.

### Understanding user groups

IAM user groups are collections of users that make it easier to manage permissions in AWS. Instead of assigning permissions to each user individually, you can assign them to a group, allowing all users in that group to have the same permissions.

### Attaching policies to user groups

I attached the policy I created to the user group, so all users in the group will be affected by it.

### Understanding IAM users

IAM users are individual identities within an AWS account that represent people or applications that need access to AWS resources. Each user can have their own sign-in credentials and permissions that control what they can access and do within AWS.

## Logging in as an IAM User

### Sharing sign-in details

The first way is email sign-in instructions or download .csv file.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed all of the cost and usage info is denied and security info. This was because of our policy we enforced onto the intern group.

![Logging in as an IAM User](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_6f2ab446)

## Testing IAM Policies

### What I did in this step

In this step, I will log into AWS using interns IAM user and test their access to production and development instance because we need to make sure they have access to development instance but not production instance.

### Testing policy actions

I tested my JSON IAM policy by logging into the IAM user account and testing the policy.

### Stopping the production instance

When I tried to stop the production instance I was met with a big you are not authorized to perform this operation error. This was because of the JSON IAM policy we created for our IAM user group.

![Testing IAM Policies](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance. it successfully stopped. This was because we allowed the users to make changes to the development instance not the production instance.

![Testing IAM Policies](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1811801c)

## IAM Policy Simulator

To extend my project, I'm going to practice another way of testing IAM policies without disrupting active in use instances. I'm doing this because we do not want to disrupt other engineers and users from instances.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is used to test policies without affecting instances for other engineers and users. It's useful for testing new policies without disrupting instances.

### How I used the simulator

I set up a simulation for our intern IAM user group to test whether they can delete tags and stop instances. The results were denied for deleting tags and allowed for stopping instances. I had to adjust the tag associated with stop instances to allow it.

![IAM Policy Simulator](https://nextwork.ai/stuart/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_069d8a621)
