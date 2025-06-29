# 🧰 How to Create a Free 4-Core ARM VM with 24GB RAM and 200GB Storage on Oracle Cloud

Oracle Cloud’s **Always Free** tier offers a generous amount of compute and storage using Ampere ARM-based instances. With careful setup, you can get up to **4 OCPUs, 24GB RAM, and 200GB block storage** completely free.

---

## 💡 What You Get for Free

According to Oracle’s [official documentation](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm):

- ✅ **Up to 4 ARM OCPUs** (Ampere A1 Flex)
- ✅ **24 GB total RAM**
- ✅ **200 GB total block storage** (boot + data volumes)
- ✅ **Up to 4 VM instances** (each must have ≥47GB boot volume)

> These resources can be used for **one large VM** or split across **multiple smaller VMs** — for example, 4× 1-core VMs with 6 GB RAM and 50 GB storage each.

---

## ⚠️ Why You Should Upgrade to Pay As You Go (PAYG)

While the resources themselves are always free, users have reported long delays or unavailability when provisioning VMs under the default Free Tier.

Community insight from [@rssnyder on GitHub](https://gist.github.com/rssnyder/51e3cfedd730e7dd5f4a816143b25dbd):

> “I personally waited **weeks** on the Free Tier without getting an ARM VM. After switching to PAYG, my VM was allocated in **three days**.”

You **won’t be charged** as long as you stay within Always Free limits.

More user experiences:
- [Reddit thread 1](https://www.reddit.com/r/homelab/comments/rzyp4l/oracle_cloud_free_tier_up_to_4_arm_vms_24gb_200gb/)
- [Reddit thread 2](https://www.reddit.com/r/oraclecloud/comments/u8ol1b/free_tier_vm_not_getting_provisioned/)
- [LowEndTalk discussion](https://lowendtalk.com/discussion/160260/oracle-cloud-free-tier/p37)

---

## 🛠️ Step-by-Step Guide

### 1. Create an Oracle Cloud Account
- Visit [https://www.oracle.com/cloud/free](https://www.oracle.com/cloud/free)
- Sign up with valid email and credit card (identity verification only)

### 2. Upgrade to Pay As You Go
- Go to Oracle Cloud Console → **Billing and Cost Management** → **Upgrade and Manage Payment**
- Choose **Upgrade to Pay As You Go**

ℹ️ This does **not** remove your Always Free eligibility

**⏳ Wait until the upgrade is confirmed. Only then proceed to the next step.**

### 3. Create an ARM VM
1. In the Console, go to **Compute → Instances → Create Instance**
2. Under **Image and Shape**, click **Change Shape**
3. Select **"Ampere" → VM.Standard.A1.Flex**
4. Choose:
   - **OCPUs**: `4` (or split it if you want more instances for free)
   - **Memory**: `24 GB` (...)
5. In **Boot Volume**, set up to `200 GB` (minimum size 50 GB)
6. Add **SSH public key** (or generate it if you don't have any)
7. Keep default networking (or create new VCN if you wan't but don't need to)
8. Click **Create**

### 4. If You Get "Out of Capacity"
- Simply try again later

---

## 🧮 Example Configurations

| VM Count | OCPUs per VM | RAM per VM | Storage per VM |
|----------|--------------|------------|----------------|
| 1        | 4            | 24 GB      | 200 GB         |
| 2        | 2            | 12 GB      | 100 GB         |
| 4        | 1            | 6 GB       | 50 GB          |

You can mix and match as long as you stay within the **global limit**:
- ≤ **4 OCPUs total**
- ≤ **24 GB RAM total**
- ≤ **200 GB block storage total**

---

## ✅ Summary

| Feature              | Always Free Limits                                          |
|----------------------|-------------------------------------------------------------|
| Compute              | 4 OCPUs (Ampere A1 Flex), 24 GB RAM                         |
| Block Storage        | 200 GB across all instances                                 |
| Max Instances        | 4 (each with ≥47 GB boot volume)                            |
| Best Practice        | Upgrade to PAYG to increase chance of successful provisioning |

---

## 📚 Sources

- [Oracle Docs: Always Free Resources](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm)
- [GitHub Gist by @rssnyder (setup & experience)](https://gist.github.com/rssnyder/51e3cfedd730e7dd5f4a816143b25dbd)
- [Reddit discussion: Oracle Free Tier experience](https://www.reddit.com/r/homelab/comments/rzyp4l/oracle_cloud_free_tier_up_to_4_arm_vms_24gb_200gb/)
- [LowEndTalk forum thread](https://lowendtalk.com/discussion/160260/oracle-cloud-free-tier/p37)
