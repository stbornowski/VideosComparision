# VideosComparision
Comparing two mp4 videos of the same work and displaying the differences for testing purposes. 

Parts to be realized:

- Reducing the complexity by using only black/white videos using ffmpeg:
  ffmpeg -i input.mp4 -vf format=gray output.mp4

- Adapting time frames between two videos (black/white videos for comparison or orginial ones):
  => syncronize_timeframes_of_videos.py

- Calculating real differences of video using black/white videos:
  => calculate_video_differences.py

- Possible alternative to calculate the difference with ffmpeg:
  ffmpeg -i video1_synced.mp4 -i video2_synced.mp4 -filter_complex "[0:v][1:v]blend=difference:1.0[out]" -map "[out]" -c:v libx264 -crf 23 difference.mp4

- Displaying the differences as color-coded in a new video:
  => visualize_diff_videos.py

- Displaying videos in side by side mode using ffmpeg:
  ffmpeg -i video1.mp4 -i video2.mp4 -filter_complex "[0:v][1:v]hstack=inputs=2[v]" -map "[v]" -c:v libx264 output.mp4
