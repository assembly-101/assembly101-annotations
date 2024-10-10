# [Fine-Grained Annotations](https://drive.google.com/drive/folders/1G1o9rTf1W5V4Q4ZSJfG2XAz0esmrwZ0g?usp=sharing)
We have 1380 fine-grained actions composed of a combination of 90 objects and 24 verbs.

The files present under the `fine-grained-annotations` folder are:
- `actions.csv`
- `train.csv`
- `validation.csv`
- `test.csv`
- `head_actions.txt`

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

- - -

### train.csv / validation.csv / test.csv
This csv provides the list of fine-grained action segments with their correponding annotations that are split between training, validation and test. The columns are:
| Column name | Type | example | Description | 
|-------------|------|---------|-------------|
| id | int | 7 | row (segment) index |
| video | str | nusar-2021_action_both_9033-a30_9033_user_id_2021-02-04_131528/C10404_rgb.mp4 | the video name in the format of {sequence_name}/{view_name}.mp4 |
| start_frame | int | 84 | #frame **(@30fps)** when the fine-grained action starts |
| end_frame | int | 111 | #frame **(@30fps)** when the fine-grained action ends |
| action_id | int | 10 | numeric action ID of the segment |
| verb_id | int | 18 | numeric verb ID of the segment |
| noun_id | int | 27 | numeric noun ID of the segment |
| action_cls | str | clap hand | action name of the segment |
| verb_cls | str | clap | verb name of the segment |
| noun_cls | str | hand | object name of the segment |
| toy_id | str | a30 | numeric ID of the toy in the segment |
| toy_name | str | suv | name of the toy in the segment |
| is_shared | bool | 0 | is the toy shared between the training and evaluation (validation/test) set? <br> `0` : not shared <br> `1` : shared <br> not shared corresponds to zero-shot classes|
| is_RGB | bool | 1 | is the view fixed (RGB) or monochrome? <br> `0` : monochrome <br> `1` : fixed (RGB)|

- - -

### test_challenge.csv (deprecated)
This csv file provides the exact test split on which our [3D Action Recognition challenge](https://codalab.lisn.upsaclay.fr/competitions/5256) is evaluated.

**Note:** The challenge on Codalab has ended. Please refer to [paperswithcode](https://paperswithcode.com/sota/3d-action-recognition-on-assembly101) for the 3D Action Recognition leaderboard. Feel free to update your `test.csv` results there.

- - -

### head_actions.txt
This text file provides the 142 head action classes among a total of 1380 fine-grained action classes. The rest are all tail classes.
