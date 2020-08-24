>[!knowledge] This Quick Start will show you how to add a scored activities to your lab. By the end you will have 2 fully functional scored activities. The scores, configuration, and contents of each item are for demonstration purposes only and may be changed to meet your exact goals. For more information on creating scored activities, please visit the complete [documentation](https://docs.learnondemandsystems.com/lod/activities.md).

## User Environment Scoring

1. Inside of the IDLx editor, cilck on the **Activity** button from the toolbar to open the Activity Manager.

    !IMAGE[activity-icon.png](./media/activity-icon.png)

1. To create a scored lab, click on the **switch** next to Enable Scoring.

1. In the **Passing Score** field add a value of **20**.

1. Click **New Automated Activity**.

    !IMAGE[activity-manager.png](./media/activity-manager.png)

1. Fill-in the basic information for your activity as follows.

    |Field|Value|Notes|
    |--|--|--|
    |Name (Optional)|++Automated Sample 1++|While the name field is optional, it is a best practice to add a name so that you may easily identify your different activities in the activity manager.|
    |Replacement Token Alias|++Sample-1++|Token Aliases must not contain spaces, it is recommended to use a - instead. This is how an activity will be referenced in your lab instructions.|
    |Instructions (Optional)|++Click the button below to recieve a score.++|Instructions within the activity are optional. Alternatively you may write any directions directly into the lab instructions.|

1. Select options to customize the activity as follows.

    |Field|Value|Notes|
    |--|--|--|
    |Scored|Selected|An activity may also be unscored for simple evaluations/assessments.|
    |Display Scripts as Task List|Unselected|If this option is selected, the On-Demand Evaluation option will no longer be available for this Activity. A best practice is often to use this option for activities with multiple scripts.
    |On-Demand evaluation|Selected|As with the Task List option, this permits a user to manually trigger an activity. If neither of these options are selected all scoring occurs at the end of the lab instance.|
    |Custom Evaluation Button Text|Selected: ++Automated Sample++|By default the activation button will say "Score" or "Check" if the activity is unscored. This allows you to define text of your choosing to display to the user.|
    |Allow Retries|Selected|If this is unselected users will only be allowed a single attempt.|
    |Required for Submission|Unselected|By selecting this, it will force users to run the activity before they may submit it for final scoring.|
    |Block Page Navigation Until Evaluated|Unselected|By selecting this users will not be allowed to progress within the lab until they have attempted the activity.|

1. In the script sections, select the target for your automated activity. This could be virtual machines, cloud subscriptions, or a container.

    !IMAGE[target-selector.png](./media/target-selector.png)

    > [!ALERT] If your lab only contains one target, you will only see 1 option in this field.

1. In the script section, set the score value to 10.

    !IMAGE[score-value.png](./media/score-value.png)

1. Based on your selected target, paste one of the below scripts into the script section:

    > [!ALERT] Windows Virtual Machines may use either PowerShell or Windows Command Line for the language (this example will use PowerShell). Linux Environments must use Bash - if PowerShell Core is installed in the Linux environment, Bash must still be selected but your script can invoke pwsh to use PowerShell within a Bash script. Cloud Subscriptions currently only support PowerShell.

    ### Windows Virtual Machine

    ```
    $desktopTxt = Get-ChildItem -Path C:\Users\Student\Desktop\ -Filter "*.txt"
    $result = $false
    if ($desktopTxt -eq $null) {
        $result = $false
        "No text files exist on the desktop."
    } else {
        $result = $true
        "At least one text file was found on the desktop."
        $desktopTxt
    }
    ```
    >[!knowledge] This script tests for the existence of a text file on the desktop. To test, create a text file on the desktop and the result should be successful.

    ---
    
    ### Linux Virtual Machine or Container

    Change the **Language** to bash, then paste the following script:

    ```
    #!/bin/bash
    #KSH

    RESULT=False

    if ( cat /etc/ssh/sshd_config |grep -i 'PermitRootLogin no' > /dev/null )
    then
        RESULT=True
    fi
    echo $RESULT
    ```
    >[!knowledge] This script tests to see if the root user has the permissions to log in via ssh. To test the script, edit the /ect/ssh/sshd_config file and change the PermitRootLogin option to **no**.

    ---

    ### Cloud Subscription (Azure)

    ```
    $LabInstanceID = "@lab.LabInstance.Id"
    $result = $false
    $resourceGroupName = "MyRG-lod${LabInstanceId}"
    $storAccount = Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name "stor${LabInstanceId}" -ErrorAction Ignore
    if ($storAccount -eq $null){
        "The Storage Account has not been created"
    } else {
        $result = $true
        "The Storage Account has  been created successfully."
    }
$result
    ```
    >[!knowledge] This script tests to see if a storage account has been created. In order to test, create a storage account named "stor@lab.LabInstance.Id". 

    ---
    
    ### Cloud Subscription (AWS)

    ```
    if ($bucket = Get-S3Bucket -BucketName "labweb-logfiles-@lab.LabInstance.Id") {
    if (($bucketloc = Get-S3BucketLocation -BucketName "labweb-logfiles-@lab.LabInstance.Id") -eq "us-east-2") {
        "Your bucket was created successfully!"
        $true
    } else {
        "Bucket was created, but is located in the wrong region!"
        $false
        }
    } else {
        "Bucket does not exist!"
        $false
    }
    ```
    >[!knowledge] This script tests to see if a specific S3 bucket has been created. In order to test, create a bucket named "labweb-logfiles-@lab.LabInstance.Id". 

1. When your activity is complete, click **Save**.

1. Inside of your IDLx instructions, insert your activity by using the lab token available in the activity manager, for this example it should be:

    ++@lab\.Activity(Sample-1)++

## Scored Question/Answer

1. Click **New Question**.

    !IMAGE[activity-manager.png](./media/activity-manager.png)

1. Fill-in the basic information for your question as follows.

    |Field|Value|Notes|
    |--|--|--|
    |Replacement Token Alias|++Question-1++|Token Aliases must not contain spaces, it is recommended to use a - instead. This is how an activity will be referenced in your lab instructions.|
    |Text|++When abbreviated, what term best represents  Learn on Demand Systems?++|Write the question that you want to present to the user.|
    |Format|Multiple choice, single answer|This is the type of question that wish to present.|

1. Select options to customize the question as follows.

    |Field|Value|Notes|
    |--|--|--|
    |Scored|++1++|An question may also be unscored for simple evaluations/assessments.|
    |On-Demand evaluation|Selected|As with the Task List option, this permits a user to manually trigger an activity. If neither of these options are selected all scoring occurs at the end of the lab instance.|
    |Custom Evaluation Button Text|Selected: ++Submit++|By default the activation button will say "Score" or "Check" if the activity is unscored. This allows you to define text of your choosing to display to the user.|
    |Allow Retries|Selected|If this is unselected users will only be allowed a single attempt.|
    |Block Page Navigation Until EvaluaAnsweredted|Unselected|By selecting this users will not be allowed to progress within the lab until they have answered the question.|

1. Click **Add Answer** and insert ++LODS++ for the answer.
1. Click **Add Answer** and insert ++ACME++ for the answer.
1. Click **Add Answer** and insert ++Learn++ for the answer.
1. Click the radio button next to the answer **LODS**, to set this as the corect answer.
1. When your question is complete, click **Save**.
1. Inside of your IDLx instructions, insert your question by using the lab token available in the activity manager, for this example it should be:

    ++@lab\.Activity(Question-1)++
