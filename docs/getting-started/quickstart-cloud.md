---
sidebar_position: 5
---

# DBOS Cloud Quickstart

Here's how to deploy a DBOS application to the cloud in a few minutes!

### Preliminaries

We assume you've already completed the [quickstart](./quickstart.md).
Before starting this tutorial, instantiate a new DBOS application and `cd` into it by running the following commands:

```bash
npx -y @dbos-inc/dbos-sdk init -n <project-name>
cd <project-name>
```

### Registration

Let's start by creating a DBOS Cloud account.
From your DBOS application directory, run the following command:

```
npx dbos-cloud register -u <username>
```

When you run the command, it will ask you for some information, then redirect you to a secure login portal.
Open the login portal in your browser and click `Confirm`, then create a new account.
After you're done, go back to the terminal.
If everything's working, the command should succeed and print `<username> successfully registered!`.


### Provisioning a Database Instance

Next, let's provision a Postgres database instance your applications can connect to!
You should choose a database name and an administrator username and password for your database instance.
Both the database instance name and the administrator username must contain only lowercase letters and numbers, dashes (`-`), and underscores (`_`).
Run this command (it should take ~5 minutes to provision):

```
npx dbos-cloud database provision <database-name> -a <admin-username> -W <admin-password>
```

If successful, the command should print `Database successfully provisioned!`.

### Registering and Deploying an Application

Now, we're ready to register and deploy your application to DBOS Cloud!
First, register your application by running this command, using your database instance name from the last step:

```
npx dbos-cloud application register -d <database-name>
```

If successful, the command should print `Successfully registered <app-name>!`

Now, deploy your application to run it in the cloud!

```
npx dbos-cloud application deploy
```

This command will build your application, then deploy it to our serverless cloud platform.
If successful, it will print `Successfully deployed <app-name>! Access your application at <URL>`
The URL should look like `https://cloud.dbos.dev/apps/<username>/<app-name>`
Your application is now live at that URL!

To see that your app is working, visit `<URL>/greeting/dbos` in your browser.
For example, if your username is `mike` and your app name is `hello`, visit `https://cloud.dbos.dev/apps/mike/hello/greeting/dbos`.
Just like in the [quickstart](./quickstart.md), you should get this message: `Hello, dbos! You have been greeted 1 times.` Each time you refresh the page, the counter should go up by one!

Congratulations, you've sucessfully deployed your first application to DBOS Cloud!