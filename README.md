# depthai_apis_synced_frames
High  level APIs to obtain synced frames using simple API calls. Implemented buffer management system to store packets until all frames arrive and flush them regularly.

## Design
A buffer is used to store streams using packet sequence number as key. Upon collecting all the streams - frameset is updated and the corresponding buffer entry is deleted. 

In the case of missing packets - buffer might accumalate incomplete packets waiting for streams. This is addressed by periodically flushing buffer if it size exceeds certain limit. However, this case has not been observed with buffer size mainitaing at 2 packets.

## Setup
1. copy all files `oakd*.py` to cloned `depthai` folder.
2. replace `depthai_helpers/mobilenet_ssd_handler.py` of depthai with this one. (landmarks and emotion recognition is made optional)
3. similarly replace `depthai_helpers/calibration_utils.py` for saving calibration information.

`oakd.py` is the API interface class.

'oakd_config.py` contains pipeline config info.

'oakd_synchronized.py` is an example template file.

`calibr_info.npz` is zipped numpy with intrinsics and distortion coefficients

Run:
`python3 oakd_syncronized.py` this should display synced resized previewout, left, right and depth_raw images.

## Testing
Tested for 10, 20, 25 and 30 fps. The buffer size does not exceed more than 2 packets, should work on low computing power devices as well.
