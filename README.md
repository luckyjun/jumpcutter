## Jumpcutter란?

Jumpcutter는 Python으로 작성된 프로그램으로 영상에서 무음 구간을 자동으로 잘라내어 편집 부담을 줄여 줍니다.
자세한 내용은 [Medium 글](https://medium.com/@emkademy/how-to-jump-cut-silent-parts-of-your-videos-automatically-with-python-2e4b96320dc1)을 참고하세요.

## 설치

```bash
pip install jumpcutter
```

## 데모

[![Watch the video](https://img.youtube.com/vi/UDjzm_lzWOA/hqdefault.jpg)](https://youtu.be/UDjzm_lzWOA)

## 사용 방법
프로그램은 11개의 명령행 인자를 받을 수 있으며 대부분 기본값이 정해져 있어 별다른 설정 없이도 사용할 수 있습니다.

1. `-i`, `--input`: jump-cut할 영상 경로
2. `-o`, `--output`: 결과 영상을 저장할 경로
3. `-m`, `--magnitude-threshold-ratio`: 오디오 신호의 최대값에 대한 무음 판단 비율 (기본값: 0.02)
4. `-d`, `--duration-threshold`: 잘라낼 무음 구간의 최소 길이(초). 예를 들어 0.5이면 0.5초 이상 지속된 무음만 제거합니다 (기본값: 0.5)
5. `-f`, `--failure-tolerance-ratio`: 분석 중 임계치를 넘는 값이 허용되는 비율 (기본값: 0.1)
6. `-s`, `--space-on-edges`: 컷팅 전후로 남길 여유 시간(초) (기본값: 0.1)
7. `-x`, `--silence-part-speed`: 무음 구간을 잘라내는 대신 x배속으로 빠르게 재생합니다
8. `-l`, `--min-loud-part-duration`: 이 값보다 짧은 음성 구간도 잘라냅니다
9. `-c`, `--cut`: `silent`, `voiced`, `both` 중 선택해 무음/음성 파트를 각각 자르거나 둘 다 저장할 수 있습니다 (기본값: silent)
10. `--codec`: ffmpeg에서 지원하는 코덱 이름. 파일 확장자로 기본값이 결정되지만 변경할 수 있습니다
11. `bitrate`: 결과 영상의 비트레이트. 잘 모르면 비워 두세요

## 실행 예시

```bash
# 가장 간단한 실행
jumpcutter -i input_video.mp4 -o output_video.mp4
# 모든 옵션을 지정한 예
jumpcutter -i input_video.mp4 -o output_video.mp4 -m 0.05 -d 1.0 -f 0.2 -s 0.2 -x 2000 -l 1.0 -c both
```
