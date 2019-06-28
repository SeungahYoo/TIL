### Git

- working copy

  수정된 파일 목록

- add

  working copy에서 check를 하는 행위

- index, staging area

  working copy에 있는 변경된 파일을 add하면 index / staging area 라는 공간으로 이동.

- commit

  index / staging area에 있는 파일들을 commit 하면 version log에 들어간다. 하나의 version이 된다.

- repository 저장소

  각각의 version이 저장되어 있는 곳.





#### 이전 상태로 돌아가기

- Reset 

  선택한 버전 이후의 버전들을 다 지운다

  - hard : 선택한 버전 이후의 상태는 폐기

  - mixed : 이후의 상태는 commit 전으로 working copy에 올려논다.

  - soft

     

- Revert 

  선택한 버전을 취소하여, 해당 버전의 이전 상태로 돌린다.

  해당 버전은 남아있고, 그 이전 상태인 새로운 커밋이 생성된다.

  가장 최신 커밋부터 순차적으로 revert 해야한다. -> 단계를 건너뛰고 revert를 하면 충돌 발생

