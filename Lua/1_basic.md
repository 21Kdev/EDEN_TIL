# 1. 주석
```lua
-- 한 줄 주석
```
```lua
--[[
    여러줄 주석
]]--
```

# 2. 변수(scope)
1. default는 global scope를 가진다.
2. local scope를 위해서는 `local`로 정의해야한다.
```lua
-- global scope
a=3 

-- local scope
if true then
    local b = 20
end
```

# 3. 변수(type)
1. `nil`: 빈 값
2. `boolean`
3. `number`: 정수, 소수점 모두 포함
4. `string`: 문자를 갖고 있으면 문자형
5. `function`
6. `table`: 여러 변수들의 그룹, Array도 table이다. 클래스처럼 활용 가능

# 4. operator
1. 수식 연산자
    * `/` : 소수점까지 계산
    * `%` : 모듈러
    * `^` : pow
2. 관계 연산자
    * `==`
    * `~=` : 다르다.
3. 논리 연산자
    * `and`
    * `or`
    * `not`
4. 특수
    * `..` : 두 문자를 붙여줌
    * `#` : 배열/테이블 갯수 count

# 5. 반복문
1. `while`(조건) `do` ~ `end`
```lua
a = 10
while (a < 20)
do
    a = a+1
end
```
2. `for` ~ `do`~ `end`
```lua
for i = 1,9,2
do
    print(i)
end
-- 1 ~ 9까지 홀수 출력, 3번째 parameter 생략시 1
```
3. `repeat` ~ `until`
```lua
a = 10
repeat
    print(a)
    a = a+1
until (a < 20)
```
4. `ipairs` / `pairs`
    * table 대상 반복

# 6. 조건문
1. `if`
```lua
a = 1
if (a > 0) then
    print('positive')
elseif (a < 0) then
    print('negative')
else
    print('0')
end

if (a > 0) then
    print('positive')
else 
    if (a < 0) then
        print('negative')
    else
        print('0')
    end
end
```

# 7. 함수
1. 파라미터로 다른 함수 받을 수 있음
2.  `...` : python의 `*args` 역할
```lua
local function hihi(a,b)
    print('hihi')
    return 123
end

hihi = function(a, b)
    print('hihi')
    return 123
end

function average(...)
    result = 0
    local arg = {...}
    
    for i,v in ipairs(arg) do 
      result = result + v 
	end 

    return result/#arg 
end 
```

# 8. String
```lua
myname = "doowon" 

print(string.upper(myname)) -- DOOWON
 
date = 3; month = 5; year = 2020 
print(string.format("Date %02d/%02d/%03d", date, month, year)) -- Date 03/05/2020, year가 %03d 이지만 4자리 전부 표시됨

print("Hello! "..myname) --  Hello! nobakee
print(string.rep("WHAT! ", 100)) -- WHAT! x100번
```

# 9. Array
1. Array의 첫번째 index가 1부터 시작함
2. 다차원 배열 사용 가능

# 10. Table
1. Lua의 유일한 자료구조이다. 
2. 여러 다른 데이터들(숫자, 문자, 함수, 다른 테이블)의 그룹
3. dictionary, array, class 처럼 사용할 수 있다.

```lua
-- 테이블에서 값에 접근하는 예시
table = {"abc" , 1, 2, name = 'kang', age = 26, 999} 
table[1] = "abc"
table[2] = 1
table[3] = 2
table[4] = 999

print(table.name) -- kang

table.name = 'Doowon' 
print(table["name"]) -- Doowon
```

# 11. Module
```lua
-- 1. module script 생성
-- 2. 테이블 선언 및 함수 정의
local mymath = {}

function mymath.add(a,b)
	print(a+b)
end

function mymath.sub(a,b) 
	print(a-b)
end 

function mymath.mul(a,b)
	print(a*b) 
end 

function mymath.div(a,b)
	print(a/b) 
end 

return mymath
```
```lua
-- table을 return 받아 module로 사용하는 법
mymathmodule = require("mymath") 
mymathmodule.add(10,20) 
mymathmodule.sub(30,20)
mymathmodule.mul(10,20) 
mymathmodule.div(30,20)
```