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

#

ECMAScript 6 = ES6 = ES2015

그 이후는 ES2016, ES2017

browser javascript 지원 확인
: http://kangax.github.io/compat-table/esnext/


#

ES6

+ var

+ const : 상수

+ let : 구문적인 변수 영역 규칙(lexical variable scoping) = 정의된 곳의 context 사용. 변수 영역을 코드 블록 안으로 한정시킬 수 있다.

+ scope : 범위, 함수 안에서 선언된 변수는 해당 함수 안에서만 사용할 수 있음. ex안의 x는 ex함수의 지역변수. 바깥의 x는 전역변수
<pre>var x = 'global';
function ex() {
    var x = 'change';
}
ex();
alert(x); // 'global'
</pre>

+ scope chain : 현재의 scope 에서 변수를 찾고 없으면, 바로 바깥 scope 에서 변수를 찾고, ... , window 객체의 변수(=전역 변수) 에서 찾고, 거기에도 없으면 undefined. / 이렇게 scope 범위를 확장하면서 변수를 찾는 관계를 scope chain

+ lexical scoping
: scope는 함수를 호출할 때가 아니라, 선언할 때 생김. = 정적 스코프 in korean.
log 안의 name은 wrapper 안의 지역변수 name이 아니라, 전역변수 name을 가리키고 있음. = lexical scoping. 함수를 처음 선언하는 순간, 함수 내부의 변수는 자기 scope에서 가장 가까운 곳에 있는 변수를 참조, 즉 2~4번째 줄에서 log 함수의 name은 전역변수 name을 참조하게 됨.
<pre>var name = 'zero';
function log() {
    console.log(name);
}
function wrapper(){
    var name = 'nero';
    log();
}
wrapper(); // zero
</pre>

+ 전역 변수를 지양. 변수가 섞일 수 있음. 혼자만 개발하는게 아님. -> 전역 변수 대신 한 번 함수 안에 넣어 지역변수로 만들어서 해결. = namespace.
<pre>var obj = {
    x: 'local';
    y: function(){
        alert(this.x);
    }
}</ore>
이렇게 해도, ojb.x = 'hacked';
로 x를 변경해버릴 수 있음.
<pre>
var another = function () {
    var x = 'local';
    function y() {
        alert(x);
    }
    return {y: y};
}
var newScope = another();
</pre>
newScope를 통해서 y에는 접근가능, x는 접근 불가.
<pre>
var newScope = (function () {
    var x = 'local';
    return function y() {
        alert(x);
    }
})();
</pre>
: IIFE(즉기 호출 함수 표현식). 모듈 패턴. 함수를 선언하자마자 바로 실행. 이 구문은 라이브러리를 만들 때 기본.

출처 : 
https://www.zerocho.com/category/JavaScript/post/5740531574288ebc5f2ba97e


#

내일 : 실행 컨텍스트 시작하기!!
출처 : https://www.zerocho.com/category/JavaScript/post/5741d96d094da4986bc950a0