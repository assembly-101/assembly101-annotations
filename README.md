# [Assembly101](https://assembly-101.github.io/) annotations

Assembly101 annotations are available [here](https://drive.google.com/drive/folders/1QoT-hIiKUrSHMxYBKHvWpW9Z9aCznJB7?usp=sharing).

The annotatations are divided into 2 granularities:
- `fine-grained-annotations`: used for Action Recognition and Action Anticipation tasks in the paper
- `coarse-annotations`: used for Temporal Action Segmentation

Frame numbers in all the annotations are provided after extracting them from the raw video at 30fps.

## Fine-Grained Annotations
We have 1380 fine-grained actions composed of a combination of 90 objects and 24 verbs.

The files present under the `fine-grained-annotations` folder are:
- `actions.csv`
- `train.csv`
- `validation.csv`
- `test.csv`
- `head_actions.txt`

## Coarse Annotations
We have 202 coarse actions composed of a combination of 61 objects and 11 verbs.

The files present under the `coarse-annotations` folder are:
- [actions.csv](#actions.csv)
- [coarse_seq_views.txt](#coarse_seq_views.txt)
- [tail_actions.txt](#tail_actions.txt)
- [coarse_labels](#coarse_labels)
- [coarse_splits](#coarse_splits)


## File structure

### actions.csv
This csv provides the list of actions and its mapping to the corresponding verbs and nouns. The columns are:
| Column name | Type | example | Description | 
|-------------|------|---------|-------------|
| id | int | 12 | row index |
| action_id | int | 380 | numeric action ID |
| verb_id | int | 7 | corresponding numeric verb ID |
| noun_id | int | 22 | corresponding numeric noun ID |
| action_cls | str | remove excavator arm | action name |
| verb_cls | str | remove | verb name |
| noun_cls | str | excavator arm | object name |

### train.csv / validation.csv
This csv provides the list of fine-grained action segments with their correponding annotations that are split between training and validation. The columns are:
| Column name | Type | example | Description | 
|-------------|------|---------|-------------|
| id | int | 7 | row (segment) index |
| video | str | nusar-2021_action_both_9033-a30_9033_user_id_2021-02-04_131528/C10404_rgb.mp4 | the video name in the format of {sequence_name}/{view_name}.mp4 |
| start_frame | int | 84 | frame when the fine-grained action starts |
| end_frame | int | 111 | frame when the fine-grained action ends |
| action_id | int | 10 | numeric action ID of the segment |
| verb_id | int | 18 | numeric verb ID of the segment |
| noun_id | int | 27 | numeric noun ID of the segment |
| action_cls | clap hand | remove excavator arm | action name of the segment |
| verb_cls | str | clap | verb name of the segment |
| noun_cls | str | hand | object name of the segment |
| toy_id | str | a30 | numeric ID of the toy in the segment |
| toy_name | str | suv | name of the toy in the segment |
| is_shared | bool | 0 | is the toy shared between the training and evaluation (validation/test) set <br> `0` : not shared <br> `1` : shared <br> not shared corresponds to zero-shot classes|
| is_RGB | bool | 1 | is the view fixed (RGB) or monochrome? <br> `0` : monochrome <br> `1` : fixed (RGB)|

### test.csv
This csv provides the list of fine-grained action segments for the test set. The labels have been withheld for the challenge purposes. The columns are:
| Column name | Type | example | Description | 
|-------------|------|---------|-------------|
| id | int | 7 | row (segment) index |
| video | str | nusar-2021_action_both_9033-a30_9033_user_id_2021-02-04_131528/C10404_rgb.mp4 | the video name in the format of {sequence_name}/{view_name}.mp4 |
| start_frame | int | 84 | frame when the fine-grained action starts |
| end_frame | int | 111 | frame when the fine-grained action ends |
| is_shared | bool | 0 | is the toy shared between the training and evaluation (validation/test) set <br> `0` : not shared <br> `1` : shared <br> not shared corresponds to zero-shot classes|
| is_RGB | bool | 1 | is the view fixed (RGB) or monochrome? <br> `0` : monochrome <br> `1` : fixed (RGB)|
