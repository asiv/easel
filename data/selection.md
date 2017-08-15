**This guide is currently still a work in progress and will be ready for the final release.**

The Easel: Visualization Recommendation System was built to recommend effective visualizations for specific questions that require data to answer. The recommendations were designed using an adapted version of Munzner's process for creating effective visualizations outlined in her book [[Visualization Analysis & Design]], which itself was a cumulation of various literature in the area of information visualization. We have adapted it based on what we found to be most useful, and filtered the information that we thought to be most pertinent for educational data and educational data usage. For a full description of how we arrived at this, please read our report published for the Higher Education Council of Ontario [To be published]. Here, we outline the adapted process. 

We have broken down our version of Munzner's process into three broad steps; Understanding the Problem, Assigning Attributes, and Refining the Visualization. 

## Step 1: Understanding the Problem
Before taking steps to visualize your data, it is important to understand what kind of data you are working with and what the kind of problem you want a visualization to help you with. Having a clear idea of what data is available and what task you want to achieve makes designing the visualization easier and helps ensure that the intended goal for the visualization is best achieved. As mentioned, there are two parts to understanding the problem: knowing what data is available and defining the task being performed by the visualization. Both are done through a process of abstraction by categories defined by Munzner. 

Data Abstraction
The overall data abstraction process required identification of the following characteristics for each visualization/questions in Table 1.

|----------------------|---------------------	|

Each item in a dataset has attributes associated with them. These are identified by considering the semantics of the data required to answer each question. This process involves consideration of the context of each question and which attributes are needed as Key attributes and which are needed as Value attributes. Keys are attribute that can uniquely identify an item, while values are characteristics about the item. In the example of the students and their assessment performance, a student number would be a key, while their mark on an assessment would be a value. The distinction between Keys and Values are not intrinsic to the data and are often driven by the Task Abstraction, which helps clarify the purpose and goal of each question or need. Keys are always connected to the items of each visualization. For simple questions, often at least one key is required for each visualization, however for more complex questions, multiple keys can be required to identify grouping attributes. Values are determined by identifying what the recorded measurements or observations would be needed to answer each question. For example, determining if a class is improving requires measuring student performance on the skill of interest. Overall, for the Easel: VRS, there were many different attributes that are identified from the list of questions, and they were heavily dependant on the context of the question.

{{Have a table for all the attribute types with examples}}

Although, technically part of Munzner's Task Abstraction, the Derive concept is important to consider when the raw data does not provide the necessary information to directly create the visualization. Derivations were often needed for determining differences, averages, etc. and should be considered additional value attributes when applicable. 

Task Abstraction
The task abstraction process helps clarify the intentions and goals of each question or data need. By considering each question abstractly, as opposed to domain-specific, the fundamental purpose can be more easily seen. This process also enables recognition of similarities between questions and the common use of visualization tools. Furthermore, task abstraction helps identify the necessary transformations of data which guides the data abstraction process. The task abstractions categories can be seen in Table 2. Other than some minor context that it provides to the Data Abstraction, it is a separate process that can be done before or after. 

|--------------	|---------------------	|

The Task Abstraction is based on two primary concepts; Actions and Targets. The purpose for a visualization should be to perform an action on a target. Targets are what a user is trying to determine from a visualization. It can be a Trend, an Outlier, or when more specific, a Feature. When dealing with attributes, the target can also be the distribution of the data, or the extreme items in the data, or when there are multiple attributes the target can be a dependency or correlation. Depending on the number of targets, your action could either be to identify a target, to compare targets, or to summarize all the targets. For example, if you were trying to see if there is an increase or decrease in graduation rates over time, you would be Identifying (action query) a Trend (target). While, if you were trying to see how one group of students were performing compared to the overall class, you would Comparing (action query) the Distributions (targets). 

An area where the task and data abstraction overlap is when considering derived data. Specifically in the case when the derived data reduces values, such as an average of the results of an assessment, or a count of students for a histogram. It is important to be clear about what target or targets are being identified or compared, so that those targets do not get reduced. For example, if the target of a visualization was a student, then you would want to avoid any reduction of students as you would when calculating the average for an assessment or bin counts for a histogram. In tabular data, like a table where each student is a row and each column is a assessment measure, one useful way to think about reduction is whether you are reducing rows (students) or columns (assessments). 

Overall, the main steps one should complete for a data-type and task:

Data Abstraction
- Determine items and attributes of data.
- Find the associated Keys and Values.
- Figure out what data needs to be derived for the task.

Task Abstraction
- Determine what the target is.
- As wether you are trying to identify a target, compare a few targets, or summarize all the targets.
- Determine whether you are looking for a specific target, and whether its location is known.

## Step 2: Assigning Attributes
Once you have completed the data abstraction process, you should a list of attributes; each that is either a key or value, and of a specific type (categorical, quantitative, etc.). In the example of {{Insert example here}}, where the task is to **{{insert task for example here}}**, the abstracted data table would be as seen in Table 3. 

**{{Insert Example Table}}**

With such a table, it can be somewhat mechanical to come up with a first pass at a visualization with the use of *visual marks* and *channels*. A mark is a basic geometric element that depicts an item. Common marks you will see are points as with scatter plots or lines like we see in bar charts. Channels are different ways that you can control a mark's appearance. Common examples you will be familiar with are position, shape and colour. We use a channel with a mark to represent magnitude (quantitative data) or identity (categorical data). Of the channels available, some channels are better than others, largely according to how well humans are able to accurately read information from them. Based on empirical research, we have available to us an ordered list of channels from most to least accurately perceivable. The list is as follows in Table 3 for magnitude and identity channels: 

Table 3: Ordered list of channels (from Figure 5.1 in Munzer)

|**Magnitude**			| **Identity**		|
|--------------			|---------------------	|
|Tilt/angle			| 			|
|Area (2D size)			| 			|
|Colour luminance		| 			|
|Colour saturation		| 			|
|Volume (3D size)		| 			|


###**Notes about Channels**: 
Notice that position is on the top of both lists, but they are actually far superior than many of the other channels and should be given special consideration and priority. Position can be a very accurate way of representing quantitative data, but by separating your marks into regions, it also is very effective in distinguishing categories. Also, some channels may interfere with each other and should be treated with care. For example, if a horizontal position channel is used on the marks in conjunction with a vertical position channel, it might look like an area channel which would have unintended consequences on the perception of the data. 

Colour should also be given special consideration since it is very commonly used. The colour channel can be separated into hue, luminance, and saturation. A colour's hue (whether it is generally blue, red, yellow, etc.) can be used with great effect to distinguish categories but is very poor at representing quantitative information. A colour's luminance and saturation (its darkness and brightness) however are useful ways of conveying quantitative information, but should be used with caution given its low ranking. While it can be used well for comparison among marks, it does not work well to accurately read quantitative information. Also, when picking colours, pay attention to whether your colour pallet works for people with colour-blindness. [ColourBrewer](http://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3) is a great resource for pallets. Additionally, a good rule of thumb is that a visualization usable in greyscale (without hues) will work with all aspects of colour incorporated. 

So now, with the table of keys and values, it is just a matter of assigning channels to values based on whether they are quantitative or categorical and going down the list based on how many of each there are. You should be making choices to ensure that the keys are still easily distinguishable however, up to the extent that the task requires. Generally, if you have 1 key, your visualization will resemble a list of some kind. A bar chart can be thought of as a list of bars, each representing a quantitative value. With 2 keys, the visualization is likely to look something like a matrix. A heat map is the most common example, where there are rows and columns for identifying keys, while the value in each cell is represented by a quantitative channel. With 3 keys, you can use a volume, but it is not recommended. Any more than three keys and you want to use more advanced techniques like recursive subdivision, where you have visualizations subdivided within visualization. 

**{{Include example of how to assign sample task and data abstractions to channels to form a visualization.}}**

Another aspect to think about when assigning values is whether the visualization should be facetted or layered. Faceting is the concept of creating multiple, similar visualization, separated by some key. When you have multiple keys, this is a good way to use a 1-key visualization multiple times. This can be especially handy when you want to compare a specific value along a key. **{Include example facetted visualization}}** Layering is another good approach, especially when the key task is comparison of targets. Layering is when you display one visualization over another, often by reducing the transparency of the visualization on top. If faceting or layering, find an order that makes sense for that grouping. There might be an implicit ordering, or if not, the number of students in each group might be a possible ordering. 

Overall, the main steps one should complete when assigning attributes: 
- Find what attributes are keys and values.
 - Determine whether values are quantitative, ordinal, or categorical.
- Assign channels in order based on values that are most important to the visualization.
 - Keep in mind choices of channels that might interfere with others.
- Decide whether the visualization requires any faceting or layering.
 - Find the order of faceting or layering.

##Step 3: Refining the Visualization
The final is somewhat different. Rather than it being about building a visualization, it is about evaluating and refining what you have. Once you have assigned channels to your different data, you might have a visualization that does or does not look similar to something you've seen before. At this point, it is important to check whether the visualization that you have created is suited for the task it was intended to help provide insight for. 

Often times, when you see a visualization you are building with the data it was made for, the information that most readily presents itself does not suit the task you were trying to gain insight on. If this is the case, there are two possible alternative routes. The first is going back to step 2 and finding other ways to represent the data in a way that more accurately and readily provides the information you are looking for. The other route is to find what it is this visualization might be useful for, and moving back to step 1. There might be an alternate question that is also worth asking that this visualization provides some insight for. The advantage here is that you already have the visualization available. Building a visualization is a highly iterative process and it is common that you might need to redo previous steps once you see a final visualization with the data you are creating. 

If the visualization does provide the kind of information you are looking for, make sure to provide all the necessary details to interpret the visualization quickly. This includes legends, labels, titles, tick marks on axis, text annotated on marks, and any other details that would make interpretation of the visualization quicker. The formatting of the visualization, such as background colour, axis grid lines and other aspects can have a significant impact on how easily information is readable. Often this can mean trying different options and seeing what works best, or even giving the eventual visualization consumers some options about how they consume the data. 