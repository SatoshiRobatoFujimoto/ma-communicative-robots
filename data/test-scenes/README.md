# Multimodal Interaction Data Representation (MIDR)

This data folder contains test data for multimodal interaction systems with robots and virtual agents. This data can be rendered by interacting system that record the interaction and it can be annotated with interpretations.

The data consists of a series of folders, each folder representing a single scenario with multimodal data files and JSON files that contain meta data on the data files and annotations of units within the multimodal data.

## Scenario structure

Each scenario contains data files for 4 possible modalities and a single corresponding JSON file that contains the meta data and the annotations for all units in that modality. Furthermore, there is a separate JSON file with the meta data on the complete scenario. This JSON file has the same name as the folder name of the scenario.

Assume our scenario folder has the name "my-first-scenario". This is how the data structure could look like:


```
my-first-scenario
	my-first-scenario.json --> overall data on the scenario
    
    #### conversations in text
	conversation-in-text.csv --> csv file with utterances from conversations that take place in this scenario
	conversation-in-text.json --> meta data and annotations on the conversation and each unit within the conversations, usually the utterances of each turn

    #### video shoot of the scenario
    interaction-video.mpeg4 --> video with the interaction
	interaction-video.json

    #### stills from the video signals
    image1.jpg --> images representing stills of situations, possibly drawn from the video
	image2.jpg
	image3.jpg
	image.json

    #### audio files possibly representing speech
    audio1.wav --> audio files representing sound events, possibly speech acts or utterances 
	audio2.wav
	audio3.wav
	audio.json
```

## Context
The file "my-first-scenario.json" describes the scenario in terms of meta data using standard data categories (Dublin core and CMDI) but also the 'spatial and temporal comtainers' with which the scenario takes place.

<ol>
    <li>Spatial container: geo-location and coordinates that define the area, possibly the name that identifies the area
    <li>Temporal container: date and begin and end time within which events take place
</ol>

The spatial and temporal containers define the primary context for interpretating any data in the scenario. In addition, the scenario can also have a specification of the participants, such as:

<ol>
    <li>Identity of the agent
    <li>Identity of the speaker
    <li>Any other people present
    <li>Objects and their spatial orientation
</ol>

In addition to the meta data, the JSON file of the scenario provides an overview of all the data files in the folder and their grounding to the spatial and temporal containers. These data files represent all the recorded signals in the scenario as its content. Each of these content file is further described in specific JSON files.

## Content
The content of the scenario is represented by a series of files in the scenario folder representing the data in different modalities. In the above example, we have separate files for the conversations, a video stream of the interaction, images of scenarios, and audio files. Each modality has a JSON file that describes the data that contain signals and any interpretation of the signal in the form of an annotation. Any signal is grounded in the spatial and temporal container using specific data elements in the JSON file. Similarly, the 

Although the data can be streamed as in video and audio, any system needs to define units within the stream to interpret states and changes between these states. Therefore, we can represent the scenario by the video itself or by a collection of stills in the form of images taken at different time points.

Through the spatial and temporal grounding of each signal, we can organise all data as a two dimensional matrix with the rows presenting temporal units and each modality as a signal column with possible data elements for each row. The next example shows a temporal ruler with 6 time points and 4 modalities of signals grounded to these units:

```
time | video | audio | text  | image |
-------------------------------------
1:02 | ...   |       |       |       |
1:03 | ...   | wav   |       | jpg   |
1:04 | ...   |       | utter | jpg   |
1:05 | ...   | wav   | utter |       |
1:06 | ...   |       |       | jpg   |
1:07 | ...   | wav   | utter |       |
```

We assume that the video is a continuous stream. The other modalities fill separate slots at time points. The temporal ruler (the first column) can have any granularity. It can be used to align the different signals across the modalities. 

## Annotations
The JSON files contain annotations of signals. Each annotation defines a segment from the signal and an interpretation label of the segements. In the case of text, segements are defined by the offsets. In the case of images, these are box coordinates.

Conversations can be represented as a CSV file with all utterances, identifiers and temporal grounding. The JSON file describes each utterance with the CSV and provided the grounding and annotations for each.

### Mentions

### Identities

### Properties and relations


