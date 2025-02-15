




```bash
find . -name "*.flac" -exec sh -c 'xld --profile "AAC Preferred Profile" -o "$(dirname "{}")" "{}"' \;
```

```bash
find . -type f -name "*.wav" -exec rm {} +
```

You can download both streams (audio and video) separately and then merge them into a single file afterward using FFmpeg. Here’s how to do it step by step:

Step 1: Download the Video

Run the following command in your Terminal to download the video stream:

ffmpeg -i "https://video.twimg.com/ext_tw_video/1890293230924615680/pu/pl/avc1/576x1024/AvCe_X7drKrz3PSJ.m3u8" -c copy video.mp4

Step 2: Download the Audio

Run this command to download the audio stream:

ffmpeg -i "https://video.twimg.com/ext_tw_video/1890293230924615680/pu/pl/mp4a/128000/LVcOzV1xP2IpN-QI.m3u8" -c copy audio.aac

Step 3: Merge Audio and Video

Now that you have both the video and audio downloaded, you can merge them into a single file:

ffmpeg -i video.mp4 -i audio.aac -c:v copy -c:a aac -strict experimental output.mp4

This will combine the video and audio streams into output.mp4.

Alternative: Combine in One Go

If you want to combine the streams directly while downloading, you can run this command:

ffmpeg -i "https://video.twimg.com/ext_tw_video/1890293230924615680/pu/pl/avc1/576x1024/AvCe_X7drKrz3PSJ.m3u8" -i "https://video.twimg.com/ext_tw_video/1890293230924615680/pu/pl/mp4a/128000/LVcOzV1xP2IpN-QI.m3u8" -c:v copy -c:a aac -strict experimental output.mp4

This approach fetches both the video and audio streams simultaneously and merges them into one file.

Explanation of Options
	•	-c copy: Copies the streams directly without re-encoding, making the process faster.
	•	-c:a aac: Ensures that the audio codec is compatible with most players.
	•	-strict experimental: Resolves potential compatibility issues when merging.

Do you want to try it all in one go, or download them separately first? Let me know if you need help!
