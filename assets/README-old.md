# Manual for EVARS-Kitchen dataset V1.0

## For each directory

(1) RGB: The raw video frames sequence of each long video. Each long video contains many action samples.
(2) Sensor: All the IMU sensor data of each action sample (already cut from the long video). The name of each file is the `narratation id`, which indicates for a single action.
(3) annotation: The orignial anottaion and pkl generation scripts, I have already run it.
(4) access: The summary files for the train set and validation set.


## For reading the samples

Your need to use the `pickle` package in python to read them:
```python
import pickle as pkl

with open('/xxx/yyy/zzz/EVARS-Kitchen/access/EVARS-train.pkl') as f:
	data = pkl.load(f)
print(data[0])
```

Each action is represented by a dict:
* `narration_id`: to specify a single action.
* `video_id`: to specify which long video does this action come from.
* `verb`/`noun`: the verb/noun label in English.
* `label_v`/`label_n`: the verb/noun label in number.
* `frame_dir`: where you could find the rgb frames.
* `start_frame`/`end_frame`: the start and the end frame index of this action in the long video.
* `sensor_dir`: where you could find the sensor data of this action.
* (`pkl_dir`: in my case, all the frames of a single action will be packed as a pkl file, this directory is where you could find those pkl files. For generating pkl file if you need, you could use `annotation/make_pickle.py` to do it.)


