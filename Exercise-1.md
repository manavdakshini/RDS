# Exercise 1: Creating an EC2 Instance and an RDS Database

**Amazon Relational Database Service (Amazon RDS)** is a web service that makes it easier to set up, operate, and scale a relational database in the AWS Cloud. It provides cost-efficient, resizable capacity for an industry-standard relational database and manages common database administration tasks.

With RDS, you can use the database products you are already familiar with like Db2, MariaDB, Microsoft SQL Server, MySQL, Oracle, and PostgreSQL. **Amazon RDS** manages backups, software patching, automatic failure detection, and recovery. In addition to the security in your database package, you can help control who can access your RDS databases. To do so, you can use AWS Identity and Access Management (IAM) to define users and permissions. You can also help protect your databases by putting them in a virtual private cloud (VPC).

You will create an **EC2 instance**, a DB instance and set up its connectivity with your EC2 instance.

## Task 1: Create an EC2 Instance to utilize as a Web Server

In this task, you will be creating an EC2 instance in the public subnet of your VPC to allow it to connect over the internet. To create the EC2 instance, follow the given steps:

1. On the AWS homepage, select the searchbar, enter **EC2** and select the AWS EC2 service as displayed in the results.

    ![](./media/ec2-searchbar.png)

1. You will be presented with the EC2 Dashboard page. Select **Launch Instance** to create an instance.

    ![](./media/ec2-launch.png)

1. On the **Launch an instance** page, provide **Web Server** as the **Name** of your EC2 instance under **Name and tags** field.

    ![](./media/ec2-name.png)

1. Under **Application and OS Images (Amazon Machine Image)**:
    - Leave **Amazon Machine Image (AMI)** to deafult as **Amazon Linux 2023 AMI**
    - Leave **Architecture** to default as **64-bit**.

    ![](./media/ec2-ami.png)

1. Keep **Instance type** to default as **t2.micro**.

    ![](./media/ec2-type.png)    

1. Under **Key pair (login)**, select **Create a new key pair** and provide **Key pair name** as **Web_Server_Key**.
    - Leave other settings to default and select **Create key pair**.

    ![](./media/ec2-keypair.png)

    >**Note:** You will be asked to download the key pair. Download it in a directory where you can access it later.

1. Under **Network Settings**:
    - Keep **Allow SSH traffic from** checkbox selected.
    - Select **Allow HTTP traffic from the internet** checkbox to access your web server instance over HTTP on the internet.
    - Leave all other network settings to default.

    ![](./media/ec2-network.png)

1. Leave all other instance settings to default and select **Launch instance** to launch the instance.

    ![](./media/ec2-launched.png)

1. Your instance will be launched. Select **View all instances** to view your running instance.

    ![](./media/ec2-view.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you have successfully validated the lab. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.
  
<validation step="84722bec-71f0-477d-a002-2ab0ec04bdd2" /> 

## Task 2: Create an an Amazon RDS database

In this task, you will create an an Amazon RDS database in the same VPC as your EC2 instance to connect with it. To create an an Amazon RDS database, follow the given steps:

1. On the searchbar, enter **RDS** and select the **RDS** service.

    ![](./media/rds-searchbar.png)

1. You will be presented with the RDS dashboard. Select **Create database** to start creating your database.

    ![](./media/RDS-create-database.png)

1. Keep **Choose a database creation method** to **Standard create** as default and select **MySQL** as the **Engine options** and keep other options as default.

    ![](./media/rds-engine.png)

1. Select **Free tier** in **Templates** field.

    ![](./media/rds-freetier.png)

1. Under **Settings**:
    - Set **DB instance identifier** to **mysql-db-instance** to identify your database instance uniquely over the region in your AWS account.
    - Keep **Master username** to **admin** as default.
    - Keep **Credentials management** to default as **Self managed** and provide a password **admin123** in the **Master password** field. Confirm the password.

    ![](./media/rds-settings.png)

1. Under **Instance configuration** section, keep everything to default and **instance class** set to **db.t3.micro**.

    ![](./media/rds-type.png)

1. Keep **Storage** settings to default. Under **Connectivity** section:
    - Select **Connect to an EC2 compute resource** and select the **Web server** in the **EC2 instance** field.
    - Keep all other connectivity settings to default.

    ![](./media/rds-connectivity.png)

    >**Note:** The database instance will be created in the same VPC where your web server instance is created. 2 new security groups will be created and attached to the database instance and web server instance separately, with rules to only allow traffic between them. A new subnet group will also be created automatically for your database instance.

1. Keep **Database authentication** option to default as **Password authentication**.

    ![](./media/rds-auth.png)

1. Under **Additional configuration**:
    - Enter **sample** for **Initial database name**
    - Uncheck the **Enable automated backups** to disable the automated backups of your DB instance.
    - Keep all other settings as default and select **Create database**.

    ![](./media/rds-add1.png)

    ![](./media/rds-creation.png)

1. **Close** the **Suggested add-ons for mysql-db-instance** flyout page. Your RDS MySQL database instance will be created in a short while. You can check your database under the **Databases** section.

    ![](./media/rds-created.png)

1. To view the endpoint of your database, select your database and check the **Endpoint & port** details under the **Connectivity & security** section.

    ![](./media/rds-endpoint.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you have successfully validated the lab. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.
  
<validation step="ee293458-e179-431f-a95c-60b3e398d5ea" /> 

**In this exercise, you have successfully created an EC2 instance as well as an RDS MySQL Instance with proper configuration to connect it to your Web Server instance.**
