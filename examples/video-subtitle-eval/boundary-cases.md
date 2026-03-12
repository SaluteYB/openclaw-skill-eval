# Boundary Cases — video-subtitle

## Case 1
- Request: 把这个采访视频提取音频并准备成可做字幕的格式。
- Expected skill: `video-subtitle`
- Why: main artifact is transcription/subtitle preparation, not a general media export.

## Case 2
- Request: 把这个视频和字幕烧在一起，导出一个成片。
- Expected skill: `video-ffmpeg`
- Why: main artifact is a new rendered media file, not subtitle-file editing.

## Case 3
- Request: 先把音频提出来，再帮我生成字幕草稿。
- Expected skill: `video-subtitle`
- Why: extraction is subordinate to subtitle/transcript workflow.

## Case 4
- Request: 把这些字幕文件按项目整理到对应文件夹里。
- Expected skill: `video-organizer`
- Why: primary action is file organization, not subtitle editing.

## Case 5
- Request: 根据字幕内容写一个 YouTube 简介。
- Expected skill: `video-publish-helper`
- Why: output is publish copy, even though subtitles are the source material.
