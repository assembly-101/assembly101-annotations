# [Coarse Annotations](https://drive.google.com/drive/folders/1sS3JNB6efBF9Payci9kpZVE4c0nybbb5?usp=sharing)

We have 202 coarse actions composed of a combination of 61 objects and 11 verbs.

The files/folders present under the `coarse-annotations` folder are:
- `actions.csv`
- `coarse_seq_views.txt`
- `tail_actions.txt`
- `coarse_labels` (folder)
- `coarse_splits` (folder)

## Folder structure
### coarse_labels
```
coarse_labels
├── assembly_nusar-2021_action_both_9011-a01_9011_user_id_2021-02-01_153724.txt
├── assembly_nusar-2021_action_both_9011-b06b_9011_user_id_2021-02-01_154253.txt
├── .
├── .
├── .
├── disassembly_nusar-2021_action_both_9011-a01_9011_user_id_2021-02-01_153724.txt
├── disassembly_nusar-2021_action_both_9011-b06b_9011_user_id_2021-02-01_154253.txt
├── .
├── .
├── .
├── disassembly_nusar-2021_action_both_9086-c14a_9086_user_id_2021-02-16_153910.txt
```

### coarse_splits
```
coarse_splits
├── train_coarse_assembly.txt
├── train_coarse_disassembly.txt
├── val_coarse_assembly.txt
├── val_coarse_disassembly.txt
├── test_coarse_assembly.txt
├── test_coarse_disassembly.txt
```

## File structure

### actions.csv
This csv provides the list of actions and its mapping to the corresponding verbs and nouns. The columns are:
| Column name | Type | example | Description | 
|-------------|------|---------|-------------|
| action_id | int | 21 | numeric action ID |
| verb_id | int | 0 | corresponding numeric verb ID |
| noun_id | int | 11 | corresponding numeric noun ID |
| action_cls | str | attach arm connector | action name |
| verb_cls | str | attach | verb name |
| noun_cls | str | arm connector | object name |

- - -

### coarse_splits/{`train/validation`}\_coarse\_{`assembly/disassembly`}.txt
This text provides the list of coarse action segments with their correponding annotations that are split between training and validation. The columns are:
| Column Number | Column name | Type | example | Description | 
|---------------|-------------|------|---------|-------------|
|0 | sequence | str | assembly_nusar-2021_action_both_9033-a30_9033_user_id_2021-02-04_132852.txt | the video name in the format of {`assembly/disassembly`}_{sequence_name}.txt |
| 1 | is_shared | str | notshared | is the toy shared between the training and evaluation (validation/test) set? <br> not shared corresponds to zero-shot classes |
| 2 | toy_id | str | a30 | numeric ID of the toy in the segment |
| 3 | toy_name | str | suv | name of the toy in the segment |
- - -

### coarse_splits/test\_coarse\_{`assembly/disassembly`}.txt
This text provides the list of coarse action segments for each sequence. The columns are:
| Column Number | Column name | Type | example | Description | 
|---------------|-------------|------|---------|-------------|
|0 | sequence | str | assembly_nusar-2021_action_both_9033-a30_9033_user_id_2021-02-04_132852.txt | the video name in the format of {`assembly/disassembly`}_{sequence_name}.txt |
| 1 | is_shared | str | notshared | is the toy shared between the training and evaluation (validation/test) set? <br> not shared corresponds to zero-shot classes |

- - -
### coarse_labels/{`assembly/disassembly`}_{sequence}.txt
This text provides the list of coarse action segments with their correponding annotations that are split between training and validation. These annotations have been withheld from the test split for challenges purposes. The columns are:
| Column Number | Column name | Type | example | Description | 
|---------------|-------------|------|---------|-------------|
| 0 | start_frame | str | 000006833 | #frame **(@30fps)** when the coarse action starts |
| 1 | end_frame | str | 000007554 | #frame **(@30fps)** when the coarse action ends |
| 2 | action_cls | str | attempt to screw chassis | action name of the segment |
- - -

### coarse_seq_views.txt
A list of all the videos that exist for a sequence in the format of {`assembly/disassembly`}_{sequence_name}/{view_name}.mp4 <br> Most of the sequences have 12 views (8 fixed and 4 egocentric), hence most of the sequences have 12 videos associated to it. <br> Please refer to [download-scripts](https://github.com/assembly-101/assembly101-download-scripts) to get a better understanding of the views and their mappings. 
- - -

### tail_actions.txt
This text file provides the 171 tail action classes among a total of 202 coarse action classes. The rest are all head classes.
