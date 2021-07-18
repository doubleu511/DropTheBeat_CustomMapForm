# DropTheBeat_CustomMapForm
게임 DropTheBeat의 유저 레코드/유저 커스텀 곡 구현에 대한 양식을 제공합니다.

* * *

### 개요

>json 파일과 이미지, 음악 파일만으로 자신의 곡을 구성해보세요.

#### 제공된 양식
- background.png
- icon.png
- ingameInfo.json
- titleInfo.json
#### 필요하지만 제공되지 않은 양식
- music.mp3<br>
음악 파일입니다. 직접 다운받으셔서 파일에 넣으셔야 합니다.
- Levels/Difficulty0.json
- Levels/Difficulty1.json
- Levels/Difficulty2.json<br>
json 파일은 아래에 후술하겠습니다.
#### 선택적 사항
- video.mp4<br>
비디오 파일입니다. 있으면 좋고 없어도 상관없습니다.

>이 양식들은 Drop The Beat 게임 빌드 파일 폴더 내에 MusicData에서도 찾아볼 수 있습니다.
<br>~~사실 직접 보는게 이거 보는거보다 빠를 수도 있습니다~~
* * *

### 적용 방식

**1. Drop The Beat 게임 빌드 파일 폴더 내에 MusicData 폴더 안으로 들어갑니다.**<br>
![1](https://user-images.githubusercontent.com/64317456/126067792-2a22abe4-81c2-4474-9d64-a3820c74206b.png)<br>
**2. 폴더를 생성하고 이름은 곡 이름으로 해둡니다. (특수문자는 권장하지 않습니다.)**<br>
![2](https://user-images.githubusercontent.com/64317456/126067891-5380be74-379a-499c-985a-511dcf0fdcca.png)<br>
**3. 이 안에 양식들을 바로 넣으면 됩니다. (Levels 이외에 다른 폴더를 만드시면 안됩니다!)**<br>
![3](https://user-images.githubusercontent.com/64317456/126067943-58e4612c-4f36-43bc-97ee-b4b99edf2a3e.png)<br>

## 적용 시 주의! 절대 파일의 이름을 바꿔선 안됩니다!
background.png, icon.png, music.mp3, video.mp4와 json파일들의 이름을 바꾸면 게임이 인식하지 못합니다.
* * *

### 파일 설명

#### Levels 폴더
- 레코드된 Difficulty json파일이 들어갈 폴더입니다.
#### background.png
- 배경 이미지 파일입니다. 1280x720, 1920x1080 정도의 사이즈가 적당합니다.
#### icon.png
- 아이콘 이미지 파일입니다. 256x256, 128x128 정도의 사이즈가 적당합니다.
#### music.mp3
- 재생될 음악 파일입니다. (올려놓지 않았습니다. 직접 다운받으셔야 합니다)
#### video.mp4
- 재생될 영상 파일입니다. (선택적 사항이며, 직접 다운받으셔야 합니다)

* * *

### titleInfo, ingameInfo json 파일 설명
곡의 정보에 맞게 해당 값들을 수정하시면됩니다.<br>

#### titleInfo.json
```jsonc
{
  "trackName": "Unity",     // 곡의 이름을 설정합니다.
  "clipStartSec": 50,       // 곡 선택 화면에서 곡이 시작할 타이밍(초)를 설정합니다.
  "signatureColor": {       // 곡 선택 화면에서 오디오 스펙트럼 색상 (RGBA)
    "r": 195,
    "g": 25,
    "b": 195,
    "a": 74
  },
  "artistName": "TheFatRat",    // 곡의 작곡가
  "difficultys": [              // 난이도 배열
    {
      "difficulty": 1,          // 난이도는 0(NORMAL), 1(HARD), 2(EXTREME)까지 가능합니다.
      "star": 1,                // 해당 난이도의 실제 난이도 값 0~11 (소수점 가능)
      "bpm": 0                  // 곡의 BPM
    }
  ],
  "designerName": "sirsirno"    // 해당 곡의 채보를 디자인한 사람
}
```

#### ingameInfo.json
```jsonc
{
  "trackName": "#1f1e33",     // 곡의 이름을 설정합니다.
  "noteColors": [             // 노트의 색상을 설정합니다. 이 색상 배열 중 랜덤으로 나오게 됩니다. (RGBA)
    {
      "r": 195,
      "g": 91,
      "b": 195,
      "a": 255
    },
    {
      "r": 195,
      "g": 130,
      "b": 195,
      "a": 255
    },
    {
      "r": 195,
      "g": 114,
      "b": 195,
      "a": 255
    },
    {
      "r": 195,
      "g": 76,
      "b": 195,
      "a": 255
    }
  ],
  "spectrumColor": {      // 오디오 스펙트럼 색상 (RGBA)
    "r": 195,
    "g": 161,
    "b": 195,
    "a": 192
  },
  "containerColor": {     // 앞쪽 노트패널 색상 (RGBA)
    "r": 195,
    "g": 89,
    "b": 195,
    "a": 177
  },
  "sideContainerColor": { // 뒤쪽 노트패널 색상 (RGBA)
    "r": 195,
    "g": 213,
    "b": 195,
    "a": 81
  },
  "clearPointScale": 1    // 클리어 게이지 배수
}
```

>json이기 때문에 복사하셨다면 주석은 모두 지우셔야 합니다.

### 레코드 방법
여기까지 오셨다면 Levels 폴더 안에 직접 짠 채보 json 파일을 넣을 차례입니다.<br>
그러기 위해선 **게임 안에 레코드 시스템을 이용하시면됩니다.**

1. 채보를 짤 mp3 파일을 준비합니다.<br>
2. 그 mp3 파일을 Drop The Beat 게임 빌드 파일 폴더 내에 MusicData/---[RecordFiles]--- 폴더 안에다가 놓으세요.<br>
![4](https://user-images.githubusercontent.com/64317456/126068914-27012559-828b-41de-b3fa-4b3cde718054.png)<br>
3. 게임을 실행하여 타이틀에서 RECORD 탭으로 들어갑니다.<br>
![5](https://user-images.githubusercontent.com/64317456/126069011-01a901ec-4aed-440c-9e67-83c06aca27d8.png)<br>
4. 레코드합니다.<br>
![6](https://user-images.githubusercontent.com/64317456/126069055-31da509b-4cdb-411c-808f-947c66e0603c.png)<br>
5. 나온 recordFile.json의 이름을 **titleInfo에서 설정한 난이도대로 바꿉니다.**<br>
![7](https://user-images.githubusercontent.com/64317456/126069164-ce597164-f0bd-4f69-8caf-215dd462cade.png)<br>
**NORMAL 이라면 Difficulty0, HARD라면 Difficulty1, EXTREME라면 Difficulty2 이런식입니다.**<br>
6. 해당 json 파일을 Levels 폴더 안으로 이동시킵니다.<br>
![8](https://user-images.githubusercontent.com/64317456/126069260-fb388285-0364-4ac6-8d62-c516007eef15.png)<br>
**titleInfo에 난이도를 배열로 만들었다면 난이도에 따른 채보를 더 추가해서 만드셔야합니다.**<br>
![9](https://user-images.githubusercontent.com/64317456/126069297-9b16ba98-cd2f-4e60-b32d-4f96c3d84bdc.png)
