chapter02 recent javascript
===

git command
<pre>git init
git add .
git commit -m "commit message"
git remote add origin "https://github.com/..."
git push origin master
</pre>

여기서 git push _**-u**_ origin master

설명 : 

git push -u origin master로 푸시하도록 안내하고 있는데 여기서 -u 옵션은 설정파일에 현재의 master 브랜치를 origin의(여기서는 fork받은 자신의 원격저장소) master 브랜치로 연결해 주어 다음부터는 자동으로 master브랜치에서 git push를 하면 origin의 master브랜치로 푸시가 되고 git pull을 하면 origin의 master를 fetch해서 로컬의 master로 merge하도록 설정하는 것이다. 그래서 .git/config파일의 내용을 보면 다음과 같이 master브랜치의 원격저장소와 머지할 브랜치가 설정되어 있는 것을 볼 수 있다.(clone을 받아오면 이 설정이 자동으로 추가된다.)

출처 : https://blog.outsider.ne.kr/866

-u 옵션을 하면 한번만 local의 origin을 원격의 master랑 연결해주는 듯?
그다음부터는 git push origin master 대신 그냥 git push 하면 되는 것 같은데ㅎㅎ