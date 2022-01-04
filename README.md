# yolov4-android-tflite

conda create -n android_yolo_v4 python==3.6.15

conda activate android_yolo_v4

# CPU
pip install -r requirements.txt

# GPU
pip install -r requirements-gpu.txt


# tf modeline çevirme
python save_model.py --weights ./data/yolov4_ders_lastt.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4 --framework tflite

# tflite modeline çevirme
python convert_tflite.py --weights ./checkpoints/yolov4-416 --output ./checkpoints/yolov4-416.tflite

# video üzerinden test
python detect_video.py --weights ./checkpoints/yolov4-416.tflite --size 416 --model yolov4 --video ./data/video.mp4 --output ./detections/video_output.avi --framework tflite
