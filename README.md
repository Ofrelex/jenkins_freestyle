# Jenkins Freestyle Project
Step-by-step process** for your Jenkins **Freestyle Project**:


## **1. Creating a Freestyle Project**

1. Log in to your **Jenkins dashboard**.
2. From the **menu on the left**, click **“New Item”**.
3. Enter a name: **`my-first-job`**.
4. Select **Freestyle project**.
5. Click **OK**.

---

## **2. Connecting Jenkins to Source Code Management (SCM)**

### On GitHub:

1. Create a new repository named **`Jenkins-scm`**.
2. Initialize it with a **README.md** file.

### On Jenkins:

1. Open **`my-first-job` → Configure\`**.
2. Under **Source Code Management**, select **Git**.
3. Paste your repository URL (e.g., `https://github.com/username/Jenkins-scm.git`).
4. Ensure **Branch Specifier** is set to `*/main`.
5. Save.
6. Click **Build Now** to verify Jenkins can pull from your repo.

---

## **3. Configuring Build Trigger (Automating Builds)**

Currently, builds are triggered manually with **Build Now**. We’ll automate it with a **GitHub webhook**.

### On Jenkins:

1. Go to **my-first-job → Configure**.
2. Scroll to **Build Triggers**.
3. Select **GitHub hook trigger for GITScm polling**.
4. Save.

### On GitHub:

1. Navigate to your repository **`Jenkins-scm`**.
2. Go to **Settings → Webhooks → Add webhook**.
3. In the **Payload URL**, enter your Jenkins URL and port:

   ```
   http://<Jenkins-IP>:8080/github-webhook/
   ```

   *(replace `<Jenkins-IP>` with your Jenkins server’s IP or domain)*.
4. Set **Content type** to `application/json`.
5. Choose **“Just the push event”**.
6. Click **Add Webhook**.

---

## **4. Testing the Setup**

1. Make a small change in your repo (edit README.md).
2. Commit and push the change to the `main` branch.
3. Go back to Jenkins → **my-first-job**.
4. Confirm a new build is automatically triggered.

---

Now, you’ve fully set up:

* A Jenkins Freestyle Project (`my-first-job`)
* Connected Jenkins to a GitHub repository (`Jenkins-scm`)
* Configured a webhook to trigger builds automatically on repo changes

---