# adapt-contrib-slider  

<img src="https://github.com/adaptlearning/documentation/blob/master/04_wiki_assets/plug-ins/images/slider01.gif" alt="Slider in action" align="right"> **Slider** is a *question component* bundled with the [Adapt framework](https://github.com/adaptlearning/adapt_framework).  

To respond to the question, the learner positions a slider along a scale. Upon submission, feedback is provided via the [**Tutor** extension](https://github.com/adaptlearning/adapt-contrib-tutor), if installed. Feedback can be provided for correct, incorrect and partially correct answers. The number of attempts allowed may be configured.

[Visit the **Slider** wiki](https://github.com/adaptlearning/adapt-contrib-slider/wiki) for more information about its functionality and for explanations of key properties. 

##Installation

As one of Adapt's *[core components](https://github.com/adaptlearning/adapt_framework/wiki/Core-Plug-ins-in-the-Adapt-Learning-Framework#components),* **Slider** is included with the [installation of the Adapt framework](https://github.com/adaptlearning/adapt_framework/wiki/Manual-installation-of-the-Adapt-framework#installation) and the [installation of the Adapt authoring tool](https://github.com/adaptlearning/adapt_authoring/wiki/Installing-Adapt-Origin).

* If **Slider** has been uninstalled from the Adapt framework, it may be reinstalled.
With the [Adapt CLI](https://github.com/adaptlearning/adapt-cli) installed, run the following from the command line:  
`adapt install adapt-contrib-slider`

    Alternatively, this component can also be installed by adding the following line of code to the *adapt.json* file:  
    `"adapt-contrib-slider": "*"`  
    Then running the command:  
    `adapt install`  
    (This second method will reinstall all plug-ins listed in *adapt.json*.)  

* If **Slider** has been uninstalled from the Adapt authoring tool, it may be reinstalled using the [Plug-in Manager](https://github.com/adaptlearning/adapt_authoring/wiki/Plugin-Manager).  
<div float align=right><a href="#top">Back to Top</a></div>

## Settings Overview

The attributes listed below are used in *components.json* to configure **Slider**, and are properly formatted as JSON in [*example.json*](https://github.com/adaptlearning/adapt-contrib-slider/blob/master/example.json). Visit the [**Slider** wiki](https://github.com/adaptlearning/adapt-contrib-slider/wiki) for more information about how they appear in the [authoring tool](https://github.com/adaptlearning/adapt_authoring/wiki). 

### Attributes

In addition to the attributes specifically listed below, [*question components*](https://github.com/adaptlearning/adapt_framework/wiki/Core-Plug-ins-in-the-Adapt-Learning-Framework#question-components) can implement the following sets of attributes:   
+ [**core model attributes**](https://github.com/adaptlearning/adapt_framework/wiki/Core-model-attributes): These are inherited by every Adapt component. They have no default values. Like the attributes below, their values are assigned in *components.json*. 
+ [**core buttons**](https://github.com/adaptlearning/adapt_framework/wiki/Core-Buttons): Default values are found in *course.json*, but may be overridden by **Slider's** model in *components.json*.

**_component** (string): This value must be: `slider`.  

**_classes** (string): CSS class name to be applied to **Slider**’s containing `div`. The class must be predefined in one of the Less files. Separate multiple classes with a space.  

**_layout** (string): This defines the horizontal position of the component in the block. Acceptable values are `full`, `left` or `right`.  

**instruction** (string): This optional text appears above the component. It is frequently used to
guide the learner’s interaction with the component.  

**_attempts** (integer): This specifies the number of times a learner is allowed to submit an answer. The default is `1`.  

**_shouldDisplayAttempts** (boolean): Determines whether or not the text set in **remainingAttemptText** and **remainingAttemptsText** will be displayed. These two attributes are part of the [core buttons](https://github.com/adaptlearning/adapt_framework/wiki/Core-Buttons) attribute group. The default is `false`.


**_questionWeight** (number): A number which reflects the significance of the question in relation to the other questions in the course. This number is used in calculations of the final score reported to the LMS.
  
**_recordInteraction** (boolean) Determines whether or not the user's response to the question will be recorded to the LMS or not. Default is `true`. For further information, see the entry for `_shouldRecordInteractions` in the README for [adapt-contrib-spoor](https://github.com/adaptlearning/adapt-contrib-spoor).

**labelStart** (string): Text/characters that appear at the start of the slider scale.    

**labelEnd** (string): Text/characters that appear at the end of the slider scale.   

**_scaleStart** (number): This value is the numeric start of the scale. It is used to calculate the slider's position on the scale.  

**_scaleEnd** (number): This value is the numeric end of the scale. It is used to calculate the slider's position on the scale.  

**_correctAnswer** (string): Used to set a single value on the slider scale as the correct answer. (Since the attribute expects a string, numeric values must appear in JSON within quotes.)

**_correctRange** (object):  Used to set a range of values on the slider scale as the correct answer. The range is determined by **_bottom** and **_top**.  

>**_bottom** (number): This number is the start value for the correct range.  

>**_top** (number): This number is the end value for the correct range.  

**_showNumber** (boolean): When set to `true`, a numeric value appears above the scale when the slider is moved. The value indicates the slider's position on the scale. The default is `true`.  

**_showScaleIndicator** (boolean): When set to `true`, a marker for the position of the slider along the scale is shown. If **_showNumber** is `true` this marker will contain a numeric value. If **_showNumber** is `false` a blank marker is shown.  

**_recordInteraction** (boolean) Determines whether the question uses SCORM cmi.interactions to track each attempt the user makes.

**_feedback** (object): If the [**Tutor** extension](https://github.com/adaptlearning/adapt-contrib-tutor) is enabled, these various texts will be displayed depending on the submitted answer. **_feedback**
contains values for three types of answers: **correct**, **_incorrect**, and **_partlyCorrect**.

>**correct** (string): Text that will be displayed when the submitted answer is correct.  

>**_incorrect** (object): Texts that will be displayed when the submitted answer is incorrect. It contains values that are displayed under differing conditions: **final** and **notFinal**. 

>>**final** (string): Text that will be displayed when the submitted answer is incorrect and no more attempts are permitted. 

>>**notFinal** (string): Text that will be displayed when the submitted answer is incorrect while more attempts are permitted.  

>**_partlyCorrect** (object): Texts that will be displayed when the submitted answer is partially correct. It contains values that are displayed under differing conditions: **final** and **notFinal**.    

>>**final** (string): Text that will be displayed when the submitted answer is partly correct and no more attempts are permitted. 

>>**notFinal** (string): Text that will be displayed when the submitted answer is partly correct while more attempts are permitted.  

### Accessibility
**Slider** has been assigned a label using the [aria-label](https://github.com/adaptlearning/adapt_framework/wiki/Aria-Labels) attribute: **ariaRegion**. This label is not a visible element. It is utilized by assistive technology such as screen readers. Should the region's text need to be customised, it can be found within the **globals** object in [*properties.schema*](https://github.com/adaptlearning/adapt-contrib-slider/blob/master/properties.schema).   
<div float align=right><a href="#top">Back to Top</a></div>

## Limitations
 
No known limitations.  

----------------------------
**Version number:**  2.0   <a href="https://community.adaptlearning.org/ target="_blank"><img src="https://github.com/adaptlearning/documentation/blob/master/04_wiki_assets/plug-ins/images/adapt-logo-mrgn-lft.jpg" alt="adapt learning logo" align="right"></a> 
**Framework versions:** 2.0  
**Author / maintainer:** Adapt Core Team with [contributors](https://github.com/adaptlearning/adapt-contrib-slider/graphs/contributors)    
**Accessibility support:** WAI AA   
**RTL support:** yes  
**Cross-platform coverage:** Chrome, Chrome for Android, Firefox (ESR + latest version), IE 11, IE10, IE9, IE8, IE Mobile 11, Safari for iPhone (iOS 7+8), Safari for iPad (iOS 7+8), Safari 8, Opera    
