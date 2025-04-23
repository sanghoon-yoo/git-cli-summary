# git-cli-summary


# 자주쓰는 GIT 명령어 모음

## 저장소 생성 및 복제/다운로드
- **새로운 저장소 생성:** `$ git init` (.git 하위 디렉토리 생성)
- **저장소 복제/다운로드(clone):**
  - `$ git clone <https:.. URL>`: 기존 소스 코드 다운로드/복제
  - `$ git clone /로컬/저장소/경로`: 로컬 저장소 복제
  - `$ git clone 사용자명@호스트:/원격/저장소/경로`: 원격 서버 저장소 복제
- **로컬 저장소 복제 설정:**
  - `$ git config (--local or --global) remote.origin.fetch +refs/heads/dev:refs/remotes/origin/dev`
  - `$ git config (--local or --global) --add remote.origin.fetch +refs/heads/master:refs/remotes/origin/master`

## 추가 및 확정(commit)
- `$ git add <파일명>`: 단일 파일의 변경 사항을 포함(인덱스에 추가된 상태)
- `$ git add *`: 파일의 변경 사항을 한 번에 모두 포함
- `$ git commit -m "커밋 메시지"`: 커밋 생성(실제 변경 사항 확정)
- `$ git commit --amend -m "커밋 메시지"`: 마지막 커밋 변경
- `$ git reset HEAD^`: 직전 commit 취소
- `$ git reset HEAD~2`: 마지막 2개의 commit을 취소
- `$ git status`: 파일 상태 확인

## 브랜치(branch) 관리
- `$ git branch`: 브랜치 목록
- `$ git branch <브랜치이름>`: 새 브랜치 생성 (로컬로 생성)
- `$ git checkout -b <브랜치이름>`: 브랜치 생성 및 이동
- `$ git checkout master`: master 브랜치로 되돌아감
- `$ git branch -d <브랜치이름>`: 브랜치 삭제
- `$ git push origin <브랜치이름>`: 만든 브랜치를 원격 서버에 전송
- `$ git push -u <remote> <브랜치이름>`: 새 브랜치를 원격 저장소로 push
- `$ git pull <remote> <브랜치이름>`: 원격 저장소의 현재 상태 다운로드 및 현재 위치한 브랜치로 병합
- `$ git push origin --delete <브랜치이름>`: 원격 저장소 브랜치 삭제

## 변경 사항 발행(push)
- `$ git push origin master`: 변경사항을 원격 서버에 업로드
- `$ git push (--force) origin TEST-2154:refs/heads/dev`: 로컬 브랜치에서 원격 저장소 브랜치로 업로드
- `$ git push (-u) <remote> <브랜치이름>`: 커밋을 원격 서버에 업로드
- `$ git remote add origin <등록된 원격 서버 주소>`: 클라우드 주소 등록 및 발행
- `$ git remote remove <등록된 클라우드 주소>`: 클라우드 주소 삭제

## 갱신 및 병합(merge)
- `$ git pull`: 원격 저장소의 변경 내용을 현재 디렉토리에 가져오고 병합
- `$ git merge <다른 브랜치이름>`: 현재 브랜치에 다른 브랜치의 수정사항 병합
- `$ git merge --no–ff <다른 브랜치이름>`: fast-forward 관계인 경우에도 병합 커밋 생성
- `$ git checkout -p <브랜치 이름> -- <파일명>`: 특정 파일 merge
- `$ git cherry-pick <커밋아이디>`: 다른 브랜치의 특정 commit 병합
- `$ git merge --abort`: 머지 컨플릭트 해결 못할 때 사용
- `$ git add <파일명>`: 각 파일을 병합 가능
- `$ git diff <브랜치이름><다른 브랜치이름>`: 변경 내용 merge 전에 바뀐 내용 비교
- `$ git rebase -i HEAD~3`: 3개의 커밋 메시지 병합 (가장 상단의 커밋 pick, 나머지는 squash)

## 태그(tag) 작업
- `$ git log`: 현재 위치한 브랜치 커밋 내용 확인 및 식별자 부여

## 로컬 변경사항 되돌리기
- `$ git checkout -- <파일명>`: 로컬 변경 사항을 변경 전으로 되돌림
- `$ git reset HEAD <파일명>`: stage에 추가된 상태 취소
- `$ git fetch origin`: 원격에 저장된 git 프로젝트의 현 상태 다운로드
- `$ git checkout <브랜치이름> <파일명>`: 특정 브랜치의 파일로 변경
- `$ git diff --no-renames --name-only HEAD <커밋아이디>`: 변경된 파일 목록 확인
- `$ git reset --hard` : 로컬 변경 사항 모두 원복
- `$ git reset --hard origin/master` : 로컬 브랜치를 원격 브랜치와 동일한 상태로 맞추기 위해 사용
- `$ git reset --hard HEAD~n : 현재 브랜치를 n 번째 이전 커밋으로 이동시키고, 스테이징 영역과 워킹 디렉토리의 모든 변경사항을 버리고 해당 커밋 상태로 완전히 되돌림
