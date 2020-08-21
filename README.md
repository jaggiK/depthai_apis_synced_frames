# depthai_apis_synced_frames
High  level APIs to obtain synced frames using simple API calls. Implemented buffer management system to store packets until all frames arrive and flush them regularly.

Setup
1. copy all files `oakd*.py` to cloned `depthai` folder.
2. replace `depthai_helpers/mobilenet_ssd_handler.py` of depthai with this one. (landmarks and emotion recognition is made optional)

`oakd.py` is the API interface class.

'oakd_config.py` contains pipeline config info.

'oakd_synchronized.py` is an example template file.

Run:
`python3 oakd_syncronized.py` this should display synced resized previewout, left, right and depth_raw images.

