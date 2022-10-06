# Handy Flow Steps
A collection of 10 custom flow steps for use with xMatters or Everbridge Flow Designer.  Each step could be of use in a variety of custom flows; none are integration specific. The steps mostly involve string manipulation, e.g. splitting and truncating. There's also a Sleep step.

The steps come packaged in a workflow with a tester form called Run Flow Step. You can try out each step and view the output via a UI form.

---------
<kbd>
  <a href="https://support.xmatters.com/hc/en-us/community/topics"><img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png"></a>
</kbd>

----------

# Pre-Requisites
* Access to Flow Designer, either via an xMatters instance or Everbridge Suite. These instructions assume you are installing on xMatters. 
* xMatters account - If you don't have one, [get one for free](https://www.xmatters.com/free)!

# Files
* [HandyFlowSteps.zip](HandyFlowSteps.zip) - xMatters workflow containing 2 forms, 1 flow canvas and 10 custom flow steps.

# Custom Flow Steps
The custom flow steps are...
*	Match Substring (Contains)

	<kbd>  <img src="/media/match_substring.png" width="250"> </kbd>
	
Use this step to see if a short string (Needle) is contained in a longer string (Haystack). Case-sensitivity is controlled via the Case Sensitive input. The step returns either true or false.

*	Sleep

	<kbd>  <img src="/media/sleep.png" width="250"> </kbd>
	
Pause execution for a few seconds mid-flow. The step outputs the number of milliseconds slept. N.B. for all flows running in the xMatters Cloud, should any individual flow execution last longer than 60 seconds, xMatters will terminate the job with a status of Canceled. However, this maximum execution time limit does not apply if the step is running on an xMatters Agent. 

*	Reverse

	<kbd>  <img src="/media/reverse.png" width="250"> </kbd>

This step reverses a string. Simple as that.

*	Concat

	<kbd>  <img src="/media/concat.png" width="250"> </kbd>

This step joins up to five smaller strings together with an optional glue characters in between. The output is a string. 

*	Split

	<kbd>  <img src="/media/split.png" width="250"> </kbd>

This step splits a string into two parts using a separator string. The output is two smaller strings. 

*	Is Field Populated

	<kbd>  <img src="/media/is_field_populated.png" width="250"> </kbd>

The step takes the output of any field as an input and returns true if it has a value, false otherwise. A numeric 0 is considered true. The Run Flow Step tester flow runs 5 of these steps in sequence, testing different field types. This is useful because it can be combined with a Switch flow step, switching on either true or false. Switches cannot test for blank input.  

*	Strip Prefix

	<kbd>  <img src="/media/strip_prefix.png" width="250"> </kbd>

This step removes a prefix from a string. The output is shorter string.

*	Truncate

	<kbd>  <img src="/media/truncate.png" width="250"> </kbd>

This step chops a string down to size. Input options allow you to specify a clean-word break and whether to include an elipses (...) at the end to indicate the text was truncated. This stops the chopped string from appearing inelegant when passing to work notes etc. As well as the truncated string, the step outputs a true/false flag called isTruncted, and a count of the number of characters removed.

*	Enrcypt

	<kbd>  <img src="/media/encrypt.png" width="250"> </kbd>

This step lets you Encrypt a string using a Salt value. 

*	Decrypt

	<kbd>  <img src="/media/decrypt.png" width="250"> </kbd>

This step lets you restore a string from the Encrypt step, provided the same Salt is used. 

<i>N.B. Encrypt-decrypt is by no means strong encryption. It's use is more for obfuscation.</i>




# Installation
1. Log into xMatters as a user with either the Developer or Full Access User role. Navigate to Workflows, click the Import button on the top right and import the [HandyFlowSteps.zip](HandyFlowSteps.zip) file.
	<kbd>  <img src="/media/handy_flow_steps.png" width="750"> </kbd>
	
2. OPTIONAL. Navigate into the new workflow. You will see a list of two forms. You will need to set Sender Permissions on the upper form, Run Flow Step. To do this, click the left most button (says <b>Web UI</b>) and then <b>Sender Permissions</b>. Add the users or roles who can use the form. We recommend allowing all those with Full Access User and Developer roles to use the form. Do the same for the lower form
	<kbd>  <img src="/media/sender_permissions.png" width="350"> </kbd>
	
3. OPTIONAL. By default, only the importing user has permission to use and modify the custom steps within the workflow. We recommend broadening permissions to allow all those with the Developer use and/or edit the flow steps, as they are useful in all sorts of situations. To do this, shift to the FLOW DESIGNER tab, just to the right of FORMS. Open the Run Flow Step flow canvas. 
	<kbd>  <img src="/media/run_flow_step_canvas.png" width="900"> </kbd>
	
4. To the right of the screen on the Palette, highlight the CUSTOM tab. Navigate to each flow step in turn. Click the gear icon then <b>Usage Permissions</b>. In the pop-up window, grant ACCESS to other users/roles as required, e.g. select the Developer role and grant permission to Edit Step.
5.  
	<kbd>  <img src="/media/step_usage_permissions.png" width="500"> </kbd>


# Testing
You can try out each new custom step via the Run Flow Step messaging form.   Navigate to Messaging > Handy Flow Steps > Run Flow Step. Choose which step to run in the first dropdown.  Each step has it’s own corresponding form section with some demo values in it. You can use the demo values supplied or over-type. 
<kbd>  <img src="/media/run_flow_step_form.png" width="900"> </kbd>
	
At the bottom of the form, you can set yourself as a Recipient. When you click Send Message, you will get an initial email notification confirming the flow has been launched. A short while later, a second email will arrive with the step’s output values clearly shown.


# Troubleshooting
Navigate to Handy Flow Steps > Flow Designer tab > Run Flow Step canvas. You can see the canvas used to select each step based on an initial Switch block. Each custom step outputs log notes. If a step fails, you can inspect the Activity Log and inspect the log messages.

<kbd>  <img src="/media/run_flow_step_activity_log.png" width="750"> </kbd>
