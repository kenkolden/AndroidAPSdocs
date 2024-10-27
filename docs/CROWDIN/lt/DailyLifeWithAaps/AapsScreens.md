# AAPS screens

```{contents} Table of Contents :depth: 2

    <br />## The Homescreen
    
    ![Homescreen V2.7](../images/Home2020_Homescreen.png)
    
    This is the first screen you will come across when you open **AAPS**, and it contains most of the information that you will need day to day.
    
    ### Section A - Tabs
    
    * Navigate between the various **AAPS** modules.
    * Alternatively you can change screens by swiping left or right.
    * Displayed tabs can be selected in [config builder](../SettingUpAaps/ConfigBuilder.md#tab-or-hamburger-menu).
    
    ### Section B - Profile & target
    
    #### Current Profile
    
    The current profile is displayed in the left bar. 
    
    Short press profile bar to view profile details. Long press profile bar to [switch between different profiles](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md#profile-switch--profile-percentage).
    
    ![Profile switch remaining duration](../images/Home2020_ProfileSwitch.png)
    
    1. Regular display with a standard profile activation.
    2. Profile switch with a remaining duration of 59mn.
    3. Profile switch with a specific percentage of 120%.
    4. Profile switch with a specific percentage of 80% and a remaining duration of 59 mn.
    5. Profile switch with a time shift of -1 hour.
    6. Profile switch with a specific percentage of 120%, time shift of 1 hour, and a remaining duration of 59mn.
    
    #### Target
    
    ![Temp target remaining duration](../images/Home2020_TT.png)
    
    Current target blood glucose level is displayed in the right bar.
    
    Short press target bar to set a **[Temporary Target](../DailyLifeWithAaps/TempTargets.md)**.
    
    If a temp target is set, the bar turns yellow and the remaining time in minutes is shown in brackets.
    
    #### Visualization of Dynamic target adjustment
    
    ![Visualization of dynamic target adjustment](../images/Home2020_DynamicTargetAdjustment.png)
    
    When using the [SMB algorithm](../SettingUpAaps/ConfigBuilder.md#aps) and [Autosens](../DailyLifeWithAaps/KeyAapsFeatures.md#autosens) functionality, **AAPS** can dynamically adjust your target based on sensitivity. 
    
    Enable either one or both of the following options in [Preferences > OpenAPS SMB settings](../SettingUpAaps/Preferences.md#openaps-smb-settings):
    
       * "sensitivity raises target" and/or 
       * "resistance lowers target" 
    
    If **AAPS** detects resistance or sensitivity, the target will change from what is set from profile. When it alters the target glucose, the background will change to green.
    
    ### Section C - BG & loop status
    
    #### Current blood glucose
    The latest blood glucose reading from your CGM is shown on the left side.
    
    The color of the BG value reflects the status to the defined [range](../SettingUpAaps/Preferences.md#range-for-visualization).
    
       * green = in range
       * red = below range
       * yellow = above range 
    
    The greyish block in the middle shows minutes since last reading and changes since last reading, in the last 15 and 40 minutes.
    
    #### Loop status
    
    ![Loop status](../images/Home2020_LoopStatus.png)
    
    On the right side, an icon shows the loop status:
    
    * Green circle = loop running
    * Green circle with dotted line = [low glucose suspend (LGS)](../SettingUpAaps/CompletingTheObjectives.md#objective-6-starting-to-close-the-loop-with-low-glucose-suspend)
    * Red circled = loop disabled (not working permanently)
    * Yellow circle = loop suspended (temporarily paused but basal insulin will be given) - remaining time is shown below icon
    * Grey circle = pump disconnected (temporarily no insulin dosage at all) - remaining time is shown below icon
    * Orange circle = super bolus running - remaining time is shown below icon
    * Blue circle with dotted line = open loop
    
    Short press or Long press the icon to open the Loop dialog to switch loop mode (Close, Low Glucose Suspend, Open or Disable), suspend / re-enable loop or disconnect / reconnect pump.
    
       * If short press on Loop icon, a validation is required after selection in Loop Dialog
    
       ![Loop status menu](../images/Home2020_Loop_Dialog.png)
    
    #### BG warning sign
    
    If for any reason, there are issues in the BG readings **AAPS** receives, you will get a warning signal beneath your BG number on the main screen.
    
    ##### Red warning sign: Duplicate BG data
    
    The red warning sign is signaling you to get active immediately: You are receiving **duplicate BG data**, which does avoid the loop to do its work right. Therefore, your loop will be disabled until it is resolved.
    
    ```{admonition} Your loop is not running
    :class: note
    Your loop is not running until you solve this issue !
    

![Red BG warning](../images/bg_warn_red.png)

You need to find out why you get duplicate BGs:

* Is Dexcom bridge enabled on your Nightscout site? Disable the bridge by going to the administration panel of your Nightscout instance, edit the "enable" variable and remove the "bridge" part there. (For heroku [details can be found here](https://nightscout.github.io/troubleshoot/troublehoot/#heroku-settings).)
* Do multiple sources upload your BG to Nightscout? If you use the BYODA app, enable the upload in **AAPS** but do not enable it in xDrip+, if you use that.
* Do you have any followers that might receive your BG but do also upload it again to your Nightscout site?
* Last resort: In **AAPS**, go to [Preferences > NSClient](../SettingUpAaps/Preferences.md#nsclient), select the sync settings and disable the "Accept CGM data from NS" option.

To remove the warning immediately and get to loop running again, you need to manually delete a couple of entries from the Dexcom/xDrip+ tab.

However, when there are a lot of duplicates, it might be easier to

* [backup your settings](../Maintenance/ExportImportSettings.md),
* reset your database in the maintenance menu and
* [import your settings](../Maintenance/ExportImportSettings.md) again

##### Yellow warning sign

The yellow warning signal is indicating that your BG arrived in irregular time intervals or that some BGs are missing. When pressing the sign, the message indicates “Recalculated data used”.

![Yellow BG warning](../images/bg_warn_yellow.png)

Usually you do not have to take any action. The closed loop will continue to work!

As a sensor change is interrupting the constant flow of BG data, a yellow warning sign after sensor change is normal and nothing to worry about.

Special note for Libre users:

* Every single libre slips a minute or two every few hours, meaning you never get a perfect flow of regular BG intervals.
* Also, jumpy readings interrupt the continuous flow.
* Therefore, the yellow warning sign will be 'always on' for Libre users.

*Note*: Up to 30h hours are taken into accord for **AAPS** calculations. So even after you solved the origin problem, it can take about 30 hours for the yellow triangle to disappear after the last irregular interval occurred.

### Skiltis D - AIO, AAO, Bazė ir Jautrumas

![Section D](../images/Home2020_TBR.png)

**Syringe**: insulin on board (IOB) - amount of active insulin inside your body

* The insulin on board figure would be zero if just your standard basal was running and there was no insulin remaining from previous boluses. 
* IOB may be negative if there have recently been periods of reduced basal.
* Press the icon to see the split of bolus and basal insulin

* **Grain**: [carbs on board (COB)](CobCalculation) - yet unabsorbed carbs you have eaten before The icon pulses red if carbs are required (see [below](#carbs-required))

* **Purple line**: current basal rate. The icon changes to reflect temporary changes in basal rate (flat at 100%) 
   * Press the icon to see the base basal rate and details of any temp basal (including remaining duration)
* **Arrows up & down**: indicating actual [Autosens](KeyAapsFeatures#autosens) status (enabled or disabled) and value is shown below icon

#### Carbs required

![Carbs required](../images/Home2020_CarbsRequired.png)

Carbs suggestions are given when the reference design detects that it requires carbs.

This is when the oref algorithm thinks it can't rescue you by zero-temping, and you will need carbs to fix.

The carb notifications are much more sophisticated than the bolus calculator ones. You might see carbs suggestion whilst bolus calculator does not show missing carbs.

Carb required notifications can be pushed to Nightscout if wished, in which case an announcement will be shown and broadcast.

### Skiltis E - Būklės indikatoriai

![Section E](../images/Home2020_StatusLights.png)

Status lights give a visual warning for

* Cannula age
* Insulin age (days reservoir is used)
* Reservoir level (units)
* Sensor age
* Battery age and level (%)

If threshold warning is exceeded, values will be shown in yellow.

If threshold critical is exceeded, values will be shown in red.

Settings can be changed in [Preferences > Overview > Status lights](../SettingUpAaps/Preferences.md#status-lights).

Depending on the pump you use, you may not have all of these icons.

### Skiltis G - Pagrindinis grafikas

![Section F](../images/Home2020_MainGraph.png)

The graph shows your blood glucose (BG) as read from your glucose monitor (CGM).

Notes entered in action tab such as fingerstick calibrations and carbs entries as well as profile switches are shown here.

Long press on the graph to change the timescale. You can choose 6, 12, 18 or 24 hours.

The green area reflects your target range.

Blue triangles show [SMB](KeyAapsFeatures#super-micro-bolus-smb) - if enabled in [Preferences > OpenAPS SMB](../SettingUpAaps/Preferences.md#openaps-smb-settings).

#### Activate optional information

On the main graph, you can switch on these optional information:

* Prognozės
* Basals
* Activity - insulin activity curve

To show this information, click the triangle on the right side of the main graph. For the main graph just the three options above the line "\---\---- Graph 1 \---\----" are available.

    ![Main graph setting](../images/Home2020_MainGraphSetting.png)
    

#### Prediction lines

* **Orange** line: [COB](CobCalculation) (color is used generally to represent COB and carbs)
   
   This prediction line shows where your BG (not where COB itself!) will go based on the current **Profile** settings, assuming that the deviations due to carb absorption remain constant. This line only appears if there are known COB.

* **Dark blue** line: IOB (color is used generally to represent IOB and insulin)
   
   This prediction line shows what would happen under the influence of insulin only. For example if you dialed in some insulin and then didn’t eat any carbs.

* **Light blue** line: zero-temp (predicted BG if temporary basal rate at 0% would be set)
   
   This prediction line shows how the BG trajectory line would change if the pump stopped all insulin delivery (0% TBR).
   
   *This line appears only when the [SMB](../SettingUpAaps/ConfigBuilder.md#aps) algorithm is used.*

* **Dark yellow** line: [UAM](../DailyLifeWithAaps/SensitivityDetectionAndCob.md#sensitivity-oref1) (un-announced meals)
   
   Unannounced meals means that a significant increase in glucose levels due to meals, adrenaline or other influences is detected. Prediction line is similar to the **orange COB line**, but it assumes that the deviations will taper down at a constant rate (by extending the current rate of reduction).
   
   *This line appears only when the [SMB](../SettingUpAaps/ConfigBuilder.md#aps) algorithm is used.*

* **Dark orange** line: aCOB (accelerated carbohydrate absorption)
   
   Similar to COB, but assuming a static 10 mg/dL/5m (-0.555 mmol/l/5m) carb absorption rate. Deprecated and of limited usefulness.
   
   *This line appears only when the older [AMA](../SettingUpAaps/ConfigBuilder.md#aps) algorithm is used.*

Usually your real glucose curve ends up in the middle of these lines, or close to the one which makes assumptions that closest resemble your situation.

#### Basals

A **solid blue** line shows the basal delivery of your pump and reflects the actual delivery over time.

The **dotted blue** line is what the basal rate would be if there were no temporary basal adjustments (TBRs).

When the standard basal rate is given, the area under the curve is shown in dark blue. When the basal rate is temporarily adjusted (increased or decreased), the area under the curve is shown in light blue.

#### Activity

The **thin yellow** line shows the activity of Insulin.

It is based on the expected drop in BG of the insulin in your system if no other factors (like carbs) were present.

### Skiltis G - papildomi grafikai

You can activate up to four additional graphs below the main graph.

To open settings for additional graphs click the triangle on the right side of the [main graph](#section-f---main-graph) and scroll down.

![Additional graph settings](../images/Home2020_AdditionalGraphSetting.png)

To add another graph check the box on the left side of its name (i.e. \---\---- Graph 1 \---\----).

Most users find the following configuration of additional graphs to be adequate :

* Graph 1 with IOB, COB, Sensitivity
* Graph 2 with Deviations and BGI.

#### Absolute insulin

Active insulin including boluses **and basal**.

#### Insulin on board

Shows the insulin you have on board (= active insulin in your body). It includes insulin from bolus and temporary basal (**but excludes basal rates set in your profile**).

If there were no [SMBs](KeyAapsFeatures#super-micro-bolus-smb), no boluses and no TBR during DIA time this would be zero.

IOB can be negative if you have no remaining bolus and zero/low temp for a longer time.

Decaying depends on your [DIA and insulin profile settings](../SettingUpAaps/YourAapsProfile.md).

#### Carbs On Board

Shows the carbs you have on board (= active, not yet decayed carbs in your body).

Decaying depends on the [deviations the algorithm detects](../DailyLifeWithAaps/CobCalculation.md).

If it detects a higher carb absorption than expected, insulin would be given and this will increase IOB (more or less, depending on your safety settings).

#### Sensitivity

Shows the sensitivity that [Autosens](KeyAapsFeatures#autosens) has detected.

Sensitivity is a calculation of sensitivity to insulin as a result of exercise, hormones etc.

#### Heart rate

This data may be available when using a [Garmin smartwatch](../UsefulLinks/WearOsSmartwatch.md#garmin).

#### Deviations

* **Grey** bars show a deviation due to carbs. 
* **Green** bars show that BG is higher than the algorithm expected it to be. Green bars are used to increase resistance in [Autosens](KeyAapsFeatures#autosens).
* **Red** bars show that BG is lower than the algorithm expected. Red bars are used to increase sensitivity in [Autosens](KeyAapsFeatures#autosens).
* **Yellow** bars show a deviation due to UAM.
* **Black** bars show small deviations not taken into account for sensitivity

#### Blood Glucose Impact

This line shows the degree to which BG ‘should’ rise or fall based on insulin activity alone.

![Homescreen buttons](../images/Screenshots_DEV_BGI.png)

It is a good combination to display this line along with the Deviation bars. They share the same scale, but it is a different one than the other optional data, so it is a good idea to display them on a separate graph, as shown above. Comparing the BGI line and the Deviation bars is another way to understand how **BG** fluctuates. Here, at the time marked **1**, the Deviation bars are greater than the BGI line, indicating that BG is rising. Later, during the hours marked **2**, BGI and DEV are pretty much in line, indicating that BG is stable.

### Skiltis H - Mygtukai

![Homescreen buttons](../images/Home2020_Buttons.png)

Buttons for Insulin, Carbs and Calculator are almost always visible. If the connection to the pump is lost, the insulin button will not be visible.

Other Buttons can be setup in [Preferences > Overview > Buttons](../SettingUpAaps/Preferences.md#buttons).

About using the Insulin, Carbs and Calculator buttons : If enabled in the [Preferences > Overview](../SettingUpAaps/Preferences.md#show-notes-field-in-treatments-dialogs), the **Notes** field allows you to enter text that will show on the main graph, and may be uploaded to Nightscout - depending on your settings for NS client.

#### Insulinas

![Insulin button](../images/Home2020_ButtonInsulin.png)

To give a certain amount of insulin without using the [bolus calculator](#bolus-wizard).

By checking the box **Start eating soon TT**, you can automatically start your [eating soon temp target](../DailyLifeWithAaps/TempTargets.md#eating-soon-temp-target).

If you do not want to bolus through the pump but record an insulin amount (i.e. insulin given by pen) check the corresponding box. When checking this box, you get an additional field “Time offset”, that you can use to record an insulin injection made in the past.

You can use the buttons to quickly increase the insulin quantity. The increment values can be changed in the [Preferences > Overview > Buttons](../SettingUpAaps/Preferences.md#buttons).

#### Angliavandeniai

![Carbs button](../images/Home2020_ButtonCarbs.png)

To record carbs without bolusing.

Certain [pre-set temporary targets](../DailyLifeWithAaps/TempTargets.md#hypo-temp-target) can be set directly by checking the box.

**Time offset**: When will you / have you been eaten carbs (in minutes).

**Duration**: To be used for ["extended carbs"](ExtendedCarbs)

You can use the buttons to quickly increase the carb amount. The increment values can be changed in the [Preferences > Overview > Buttons](../SettingUpAaps/Preferences.md#buttons).

#### Skaičiuotuvas

See Bolus Wizard [section below](#bolus-wizard).

#### Calibrations

Sends a calibration to xDrip+ or opens Dexcom calibration dialogue.

Must be activated in [Preferences > Overview > Buttons](../SettingUpAaps/Preferences.md#buttons).

#### NGJ

Opens xDrip+.

Back button returns to **AAPS**.

Must be activated in [Preferences > Overview > Buttons](../SettingUpAaps/Preferences.md#buttons).

#### Quick Wizard

Easily enter amount of carbs and set calculation basics.

Details are set up in [Preferences > Overview > QuickWizard settings](../SettingUpAaps/Preferences.md#quick-wizard).

## Boluso skaičiuotuvas

![Bolus wizard](../images/Home2020_BolusWizard_v2.png)

When you want to make a meal bolus, this is where you will normally make it from.

### Skiltis I

Shows the calculated bolus.

If the amount of insulin on board already exceeds the calculated bolus then it will just display the amount of carbs still required.

### Skiltis J

BG field is normally already populated with the latest reading from your CGM. If you don't have a working CGM then it will be blank.

In the **Carbs** field, you add your estimate of the amount of carbs - or equivalent - that you want to bolus for.

The **Corr** field is if you want to modify the end dosage for some reason.

The **Carb time** field is for pre-bolusing so you can tell the system that there will be a delay before the carbs are to be expected. You can put a negative number in this field if you are bolusing for past carbs.

**Eating reminder** : For carbs in the future, the alarm checkbox can be selected (and is by default when a time in the future is entered) so that you can be reminded at the given time, when to eat the carbs you have input into **AAPS**.

![BolusWizard with Eating Reminder](../images/Home2021_BolusWizard_EatingReminder.png)

### Skiltis K

**Profile** allows you to select a different profile than the current one, to make the calculation for the insulin required. This profile selection applies only for the current bolus, it is not a profile change.

**Super Bolus** is where the basal insulin for the next two hours is added to the immediate bolus and a zero TBR is issued for the following two hours to take back the extra insulin. The option only shows when "Enable Superbolus in wizard" is set in the [Preferences > Overview > Advanced Settings](../SettingUpAaps/Preferences.md#advanced-settings-overview). The idea is to deliver the insulin sooner and hopefully reduce spikes.

For details visit [diabetesnet.com](https://www.diabetesnet.com/diabetes-technology/blue-skying/super-bolus/).

### Skiltis L

Details of the wizard's bolus calculation.

You can deselect any that you do not want to include, but you normally wouldn't want to.

For safety reasons the **TT box must be ticked manually**, if you want the bolus wizard to calculate based on an existing temporary target.

#### Combinations of COB and IOB and what they mean

* For safety reasons, the IOB box cannot be unticked when COB box is ticked as you might run the risk of too much insulin as **AAPS** is not accounting for what’s already given.
* If you tick COB and IOB, unabsorbed carbs that are not already covered with insulin + all insulin that has been delivered as TBR or SMB will be taken into account.
* If you tick IOB without COB, **AAPS** takes account of already delivered insulin but won’t cover that off against any carbs still to be absorbed. This leads to a 'missing carbs' notice.
* If you bolus for **additional food** shortly after a meal bolus (i.e. additional desert) it can be helpful to **untick all boxes**. This way just the new carbs are being added as the main meal won't necessarily be absorbed so IOB won't match COB accurately shortly after a meal bolus.

![BolusWizard with Details](../images/Home2021_BolusWizard_Details.png)

The box near the eye allows you to choose between the detailed view, with the numbers entering the calculation for each item, or the simple view with icons. Pressing on an icon will enable / disable this entry from the calculation.

#### Wrong COB detection

![Slow carb absorption](../images/Calculator_SlowCarbAbsorption.png)

If you see the warning above after using bolus wizard, **AAPS** has detected that the calculated COB value may be wrong. So, if you want to bolus again after a previous meal with COB, you should be aware of overdosing!

For details, see the hints on [COB calculation page](CobCalculation#detection-of-wrong-cob-values).

## Action tab

![Actions tab](../images/Home2021_Action.png)

### Actions - section M

Button **[Profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md#profile-switch--profile-percentage)** as an alternative to pressing the [current profile](#section-b---profile--target) on homescreen.

Button **[Temporary target](../DailyLifeWithAaps/TempTargets.md)** as an alternative to pressing the [current target](#section-b---profile--target) on homescreen.

Button to start or cancel a temporary basal rate. Please note that the button changes from “TEMPBASAL” to “CANCEL x%” when a temporary basal rate is set.

Even though [extended boluses](ExtendedCarbs#extended-bolus-and-why-they-wont-work-in-closed-loop-environment) do not really work in a closed loop environment some people were asking for an option to use extended bolus anyway.

* This option is only available for Dana RS and Insight pumps. 
   * Closed loop will automatically be stopped and switched to open loop mode for the time running extended bolus.
   * Make sure to read the [details](ExtendedCarbs) before using this option.

### Careportal - section N

Displays information on:

    * sensor age & level (battery percentage)
    * insulin age & level (units)
    * cannula age
    * pump battery age & level (percentage
    

Less information will be shown if **low resolution skin** is used ([Preferences > General > Skin](../SettingUpAaps/Preferences.md#skin)).

#### Sensor level (battery)

Works for CGM with an additional transmitter such as MiaoMiao 2. (Technically sensor has to send cat level information to xDrip+.)

Thresholds can be set in [Preferences > Overview > Status lights](../SettingUpAaps/Preferences.md#status-lights).

If the sensor level is the same as the phone battery level, your xDrip+ version is probably too old and needs an update. (Needs xDrip+ nightly build Dec. 10, 2020 or newer.)

    ![Sensor levels equals phone battery level](../images/Home2021_ActionSensorBat.png)
    

### Careportal - section O

BG check, prime/fill, sensor insert and pump battery change are the base for the data displayed in [section N](#careportal---section-n).

Prime/Fill allows you to record pump site and insulin cartridge change.

Section O reflects the Nightscout careportal. So exercise, announcement and question are special forms of notes.

### Tools - section P

#### History Browser

Allows you to ride back in **AAPS** history.

#### BPD

Total daily dose = bolus + basal per day

Some doctors use - especially for new pumpers - a basal-bolus-ratio of 50:50.

Therefore, ratio is calculated as TDD / 2 * TBB (Total base basal = sum of basal rate within 24 hours).

Others prefer range of 32% to 37% of TDD for TBB.

Like most of these rules-of-thumb it is of limited real validity. Note: Your diabetes may vary!

![History browser + TDD](../images/Home2021_Action_HB_TDD.png)

## Insulin Profile

![Insulin Profile](../images/Screenshot_insulin_profile.png)

This shows the activity profile of the insulin you have chosen in [config builder](../SettingUpAaps/ConfigBuilder.md#insulin).

The **purple** line shows how much insulin remains after it has been injected as it decays with time and the **blue** line shows how active it is. The important thing to note is that the decay has a **long tail**. If you have been used to manual pumping, you have probably been used to assuming that insulin decays over about 3.5 hours. However, when you are looping, the long tail matters as the calculations are far more precise and these small amounts add up when they are subjected to the recursive calculations in the **AAPS** algorithm.

For a more detailed discussion of the different types of insulin, their activity profiles and why all this matters you can read an article here on [Understanding the New IOB Curves Based on Exponential Activity Curves](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/understanding-insulin-on-board-calculations.html#understanding-the-new-iob-curves-based-on-exponential-activity-curves)

And you can read an excellent blog article about it here: [Why we are regularly wrong in the duration of insulin action (DIA) times we use, and why it matters…](https://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/)

And even more at: [Exponential Insulin Curves + Fiasp](https://web.archive.org/web/20220630154425/http://seemycgm.com/2017/10/21/exponential-insulin-curves-fiasp/)

## Pump Status

![Pump Status](../images/Screenshot_PumpStatus.png)

* Different information on pump status. Displayed information depends on your pump model.
* See [pumps page](../Getting-Started/CompatiblePumps.md) for details.

## Loop, AMA / SMB

These tabs show details about the algorithm's calculations and why **AAPS** acts the way it does.

Calculations are run each time the system gets a fresh reading from the CGM.

For more details see [APS section on config builder page](../SettingUpAaps/ConfigBuilder.md#aps).

## Profile

![Profile](../images/Screenshots_Profile.png)

Profile contains information on your individual diabetes settings:

    * DIA (Duration of Insulin Action)
    * IC or I:C: Insulin to Carb ratio
    * ISF: Insulin Sensitivity Factor
    * Basal rate
    * Target: Blood glucose level that you want **AAPS** to be aiming for
    

See the detailed **[Profile](../SettingUpAaps/YourAapsProfile.md)** page for more information.

## Automatizavimas

See the dedicated page [here](../DailyLifeWithAaps/Automations.md).

## NSClient

![NSClient](../images/Screenshots_NSClient.png)

This page displays the status of the connection with your Nightscout site.

Settings can be changed in [Preferences > NS Client](../SettingUpAaps/Preferences.md#nsclient).

For troubleshooting see this [page](../GettingHelp/TroubleshootingNsClient.md).

## BG Source - xDrip+, BYODA...

![BG Source tab - here Nightscout](../images/Screenshots_BGSource.png)

Depending on your BG source settings, this tab is named differently.

Shows history of CGM readings and offers option to remove reading in case of failure (i.e. compression low) or duplicate readings.

## Terapija

This view can be accessed by pressing the 3 dots on the right of the menu, then Treatments. It is not possible to show it in the main menu through the Config Builder. In this view, you can view and alter the history of the following treatments:

* Bolus & carbs
* [Ištęstas bolusas](../DailyLifeWithAaps/ExtendedCarbs.md#extended-bolus-and-switch-to-open-loop---dana-and-insight-pump-only)
* Temporary basal rate
* [Temporary target](../DailyLifeWithAaps/TempTargets.md)
* [Profilio keitimas](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md)
* Careportal: notes entered through action tab and notes in dialogues
* User entry: other notes that are not sent to Nightscout

In the last column, the data source for each line is displayed in blue. It can be :

* NS for Nightscout : the data comes from or has been recorded to Nightscout
* PH for Pump History : the data has been processed by the pump

### Bolus & carbs

![Carbs & bolus](../images/TreatmentsView1.png)

On this tab you can view the bolus and carbs log. Each bolus (line **1** and **4**) shows the remaining associated IOB next to the insulin amount. The origin of the bolus can be either :

* Meal (manually entered though the Insulin, Quick Wizard or Bolus Wizard buttons)
* SMB, when using the SMB Functionality

The carbs (line **2**) are only stored in Nightscout. If you have used the [Bolus Wizard](#bolus-wizard) to calculate insulin dosage, you can press the “Calc” text (line **3**) to show the details of how the bolus was calculated.

Depending on the pump used, insulin and carbs can be shown in one single line, or will result in multiple lines: one for the calculation detail, one for the carbs, one for the bolus itself.

The treatment tab can be used to correct faulty carb entries (*i.e.* you over- or underestimated carbs). Note that it is not possible to edit an existing entry, you need to follow the following process:

1. Patikrinkite ir įsidėmėkite esamą aktyvių angliavandenių AAO ir aktyvaus insulino AIO kiekį, rodomą pagrindiniame ekrane.
2. Priklausomai nuo pompos modelio, angliavandeniai rodomi kartu su insulinu vienoje eilutėje arba kaip atskiras įrašas (pvz., Dana RS).
3. Remove the entry with the faulty carb amount. (Latest versions have trashcan icon in treatments screen. Press the trashcan icon, select the lines to remove, and then press the trashcan icon again to finalize.)
4. Patikrinkite aktyvių angliavandenių kiekio AAO įrašą pagrindiniame ekrane - šitaip įsitikinkite, kad angliavandeniai buvo sėkmingai ištrinti.
5. Atlikite tą patį su aktyviu insulinu AIO, jei skirtuke „Įrašai“ matote angliavandenius ir insuliną vienoje eilutėje.
   
   → If carbs are not removed as intended, and you add additional carbs as explained here (6.), COB will be too high and that might lead to too high insulin delivery.

6. Įvesite teisingą angliavandenių kiekį per AV mygtuką pagrindiniame ekrane ir įsitikinkite, kad teisingai įvedėte valgymo laiką.

7. Jei skirtuke „Įrašai“ matote vienoje eilutėje angliavandenius ir insuliną, taip pat turite iš naujo įvesti insulino kiekį. Atkreipkite dėmesį į tinkamo laiko pasirinkimą ir tada pradžios ekrane patikrinkite aktyvaus insulino AIO duomenis.

### Temp Basal

![Temp Basal](../images/TreatmentsView2.png)

The **temp basals** applied by the loop are shown here. When there is still an impact on the IOB for an entry, the information is shown in green. It can be:

* Positive IOB if the temp basal was higher than the one set in the Profile (line **2**)
* Negative IOB for a zero-temp or if the temp basal was lower than the one set in the Profile (line **1**)

Deleting the entries only affects your reports in Nightscout and will probably tamper your real IOB - it is not recommended.

On the left of a line, a red S means “Suspend” : it happens when basal is not currently delivered. This is a normal situation when in the process of changing a pod, for example.

### Temporary target

![Temporary target](../images/TreatmentsView3.png)

The history of temporary targets can be seen here.

### Profile Switch

![Profile Switch](../images/TreatmentsView4.png)

The history of profile switches can be seen here. You may see multiple entries each time you switch profile : line **1**, stored in Nightscout but not in Pump History, corresponds to the request of a profile switch made by the user. Line **2**, stored both in NS and PH, correspond to the actual switch.

Deleting the entries only affects your reports in Nightscout and will never actually change the current profile.

### Care portal

![Care portal](../images/TreatmentsView5.png)

This tab shows all notes and alerts recorded in Nightscout.

## History Browser

This view can be accessed by pressing the 3 dots on the right of the menu, then History. It is not possible to put in the main menu through the Config Builder. It can also be accessed through a button at the bottom of the [Action tab](#action-tab).

Allows you to ride back in **AAPS** history.

## Profile Helper

This view can be accessed by pressing the 3 dots on the right of the menu, then Profile Helper. It is not possible to put in the main menu through the Config Builder. The [Profile Helper](../SettingUpAaps/ProfileHelper.md) can help you:

* build a profile from scratch for a kid
* compare two profiles
* clone a profile