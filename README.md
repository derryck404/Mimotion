# Github Actions Deployment Guide on ZeppLife For Email
![Mimotion compliant](https://img.shields.io/badge/%F0%9F%95%B6-Mimotion%F0%9F%8F%83%E2%80%8D%E2%99%82%EF%B8%8F-blue?labelColor=f46db0)



## 💻Install
This project uses [python](http://python.org), but they are not locally installed. Just **FORK THIS REPOSITORY**.



## 📌Usage
-  Fork this repository.  
-  Set Actions secrets and variables in the repository settings.  
-  Click Actions, run the Brush Steps Workflow.
  
   - Set the secrets **`PAT`**, **`AES_KEY`**, **`CONFIG`** in [Settings](https://github.com/derryck404/mimotion/settings/variables/actions). From **Settings-->Secrets and variables-->Actions-->New repository secret**.

     | Secrets  | Format   |
     |----------|----------|
     | PAT      | The value of PAT is [Fine-grained tokens](https://github.com/settings/personal-access-tokens/new) you need to apply, and select **`Only select repositories`**. It needs **`Actions`**, **`Contents`**,**`Metadata`** and **`Workflows`** Access **`Read and write`** permission  |
     | AES_KEY  | For multiple accounts, set a non-Chinese string with a length of 16 characters, run the [Brush Steps](https://github.com/derryck404/Mimotion/actions/workflows/run.yml) workflow twice  |
     | CONFIG   | Set the user key **`USER`**, **`PWD`**, **`MIN_STEP`**, **`MIN_STEP`** and others fileds  |

      >The configuration content of **`CONFIG`** is as follows.
        ```json
         {
          "USER": "abcxxx@xx.com",
          "PWD": "password",
          "MIN_STEP": "18000",
          "MAX_STEP": "25000",
          "PUSH_PLUS_TOKEN": "",
          "PUSH_PLUS_HOUR": "",
          "PUSH_PLUS_MAX": "30",
          "SLEEP_GAP": "5",
          "USE_CONCURRENT": "False"
        }
       ```

     | KeyName         | Format                                                                                                 |
     |-----------------|--------------------------------------------------------------------------------------------------------|
     | USER            | Fill in the **ZeppLife account** email address, only support email account registration login          |
     | PWD             | Fill in the password corresponding to your **ZeppLife account**                                        |
     | MIN_STEP        | Minimum steps                                                                                          |
     | MAX_STEP        | Maximum steps. Reaching its maximum value at 22:00 UTC+8                                               |
     | PUSH_PLUS_TOKEN | Fill in [Pushplus](https://www.pushplus.plus) token                                                    |
     | PUSH_PLUS_HOUR  | Set **Pushplus** scheduled push notification, the value is an integer, if not pushed immediately       |
     | PUSH_PLUS_MAX   | Set the maximum number of account details that **Pushplus** can push. The default value is 30          |
     | SLEEP_GAP       | The interval for executing tasks with multiple accounts, in seconds. The default value is 5            |
     | USE_CONCURRENT  | Enable multi-threading experimental features. Fill in **`True`**, then **`SLEEP_GAP`** will be invalid |
 
   - Manually run the [Brush Steps](https://github.com/derryck404/Mimotion/actions/workflows/run.yml) workflow. Click **`Run workflow`** to trigger the execution, view the execution record, and verify whether it is configured correctly.


   
## 🛠Optional Settings

- **Customize multiple accounts** 
  >To use multiple accounts, please split with **`#`** and save to the variables **USER** and **PWD**
  ```json
  {
    "USER": "12345@qq.com#54321@qq.com",
    "PWD": "abc123qwe#abcqwe2",
    "MIN_STEP": "18000",
    "MAX_STEP": "25000"
  }
  ```

- **Customize start time** 
  >Set the Variables **`CRON_HOURS`** in [Settings](https://github.com/derryck404/mimotion/settings/variables/actions). From **Settings-->Secrets and variables-->Actions-->New repository variables**.
  ```yaml
  UTC: 0,2,4,6,8,14
  UTC+8: 8,10,12,14,16,22
  ```

 
## ⌛Update
- Click **`Sync fork`** on the repository interface, click **`Update branch`** and wait for synchronization to complete.
- Back up the **Code[`encrypted_tokens.data`](https://github.com/derryck404/Mimotion/blob/master/encrypted_tokens.data)** in advance when **`AES_KEY`** is configured. Resubmit it to the repository after the update is completed.



## 🔔Notes
- This Github Action run six times a day, which controlled by **`cron`** in **Code [run.yml](https://github.com/derryck404/Mimotion/blob/master/.github/workflows/run.yml)**. The variable `minute` is random values.
- Please be sure to match the username and password of multiple accounts, otherwise it will not work.  
- The start time must be **UTC Time**.  
- If Alipay has not updated the step count, please go to **ZeppLife ---> Settings ---> Account ---> Delete Account ---> Clear Datas**, then log in again and rebind the third party authentication.  
- ZeppLife will not update the step count, only the associated ones will be synchronized.  
- Please note that the account is **ZeppLife account**.  
- The maximum and minimum steps increase over time and reach their maximum value at 22:00 Beijing time. To change this range, modify **`MIN_STEP`** and **`MAX_STEP`** in **Code [run.yml](https://github.com/derryck404/Mimotion/blob/main/.github/workflows/run.yml)**.



## 💌Contributing
This project is originated fork from [@TonyJiangWJ](https://github.com/TonyJiangWJ/mimotion), which modified from [@xunichanghuan](https://github.com/xunichanghuan/), [@huangshihai](https://github.com/huangshihai/mimotion) and [@hanximeng](https://github.com/hanximeng/Zepp_API/). Many thanks for their contribution to the project.

<a href="https://github.com/TonyJiangWJ/"><img src="https://avatars.githubusercontent.com/u/11325805?v=4" width="50" height="50" style="border-radius:50%; overflow:hidden;"/></a>
<a href="https://github.com/xunichanghuan/"><img src="https://avatars.githubusercontent.com/u/9484015?v=4" width="50" height="50" style="border-radius:50%; overflow:hidden;"/></a>
<a href="https://github.com/huangshihai/"><img src="https://avatars.githubusercontent.com/u/23566676?v=4" width="50" height="50" style="border-radius:50%; overflow:hidden;"/></a>
<a href="https://github.com/hanximeng/"><img src="https://avatars.githubusercontent.com/u/28382753?v=4" width="50" height="50" style="border-radius:50%; overflow:hidden;"/></a>
