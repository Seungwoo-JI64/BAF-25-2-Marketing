# BAF-25-2-Marketing
비어플 25년 2학기 마케팅

# 깃허브 사용 방법
모든 작업은 VScode 터미널에서 진행
## 파일 작업
1. `git clone https://github.com/Seungwoo-JI64/BAF-25-2-Marketing.git BAF-25-2-Marketing`  
&nbsp;깃허브에 업로드되어있는 모든 데이터를 **최초**로 다운로드  
현재 작업공간에 `BAF-25-2-Marketing`이름의 폴더가 생성, 이후 `cd`명렁어를 이용하여 해당 폴더로 작업공간 이동  
2. `git add .` 또는 `git add "작업 파일"`  
&nbsp; 작업을 진행한 파일을 로컬 git 저장소로 이동, 만약 해당 진행사항을 취소시킬려면 `git reset`  
3. `git commit -m "커밋 메세지"`  
&nbsp;수정한 파일을 설명하는 커밋 메세지를 작성  
4. `git push origin "브랜치명"`  
&nbsp;현재 작업중인 파일을 add한 브랜치를 깃허브에 업로드  
이후 깃허브의 주인이 해당 파일을 확인 후 main으로 업로드함  

## 브랜치
가장 중심에 main브랜치가 있다. 개인은 각자 자신만의 브랜치(곁다리)에서 작업을 진행하여 main의 파일을 망치는 일이 없어야 한다.  
각자 브랜치에서의 작업을 마치면, 최종 확인 후 확실한것만 main에 합쳐야 한다.  
1. `git branch <새로운_브랜치_이름>`  
&nbsp;자신만의 새로운 브랜치를 생성한다  
2. `git checkout <이동할_브랜치_이름>`  
&nbsp;작업을 진행할 브랜치로 이동한다  
3. `git merge <병합_대상_브랜치>`  
&nbsp;병합을 당할 브랜치로 이동한 상태에서, 병합을 위해 데이터를 가져올 브랜치를 지정한다. (아래에 재차 설명)  

## add하기 전
자신의 로컬 환경에서 push를 할때, 이미 다른 사람이 깃허브의 main에 변경사항을 업로드 하였다면 push가 안된다.  
자신이 수정한 파일을 다른 사람이 동시에 작업한 것이 아닌 이상, 해당 변경사항을 미리 로컬에 병합하여야 한다.  
1. main 브랜치로 이동  
2. `git fetch origin main`  
&nbsp;깃허브(origin)의 main브랜치를 로컬로 가져온  
3. `git merge origin/main'  
&nbsp;로컬의 main브랜치에 깃허브의 main작업을 병합함  
4. 작업을 진행하던 브랜치로 이동  
5. `git merge main`  
&nbsp;현재 작업중인 브랜치에 main파일을 병합함 (이때 자신이 작업중이던 파일은 겹치지만 않는다면 그대로 유지됨)  
6. 이후 자신의 브랜치를 깃허브에 `add, commit, push`

## 대용량 파일 다운로드
깃허브는 100mb이상의 파일은 업로드 하지 못한다. 따라서 lfs서버에 우회하여 업로드 하여야 한다.
1. `git lfs install`  
lfs를 설치한다
2. `git lfs pull`  
처음 clone을 했다면 이것을 사용하지 않아도 된다. 그러나 lfs서버에 새로 업로드된것만을 가져오고 싶다면 이것을 사용할 것.

대용량 파일을 로컬에서 깃허브로 업로드할려면  
3. `git lfs track "경로/파일명.확장자"` (또는 한 종류의 확장자를 전부 업로드 하는 방법도 있지만, 이것은 모든 파일을 대상으로 하므로 주의 필요)  
4. `git add .gitattributes`  
5. `git commit -m "커밋메세지"`  
6. `git add .` 이후 `commit`, `push` 동일 (add . 해도 괜찮다 - 대용량 파일은 이미 lfs에 인식되었기 때문)
