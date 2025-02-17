# Monkey_Compiler
- 가상머신
    - 운영체제, 하드웨어와 상관없이 프로그램을 동작할 수 있게 해줌.
    - 특정 도메인에 특화되어서 성능이 더 잘 나올 수 있다.
- 1 + 2
    - 렉서 → 파서 → 컴파일러 → 가상머신
    - 문자열 → 토큰 → AST → 바이트코드 → 객체
    - 위와같은 순으로 변환 단계를 거침
    - 컴파일 타임 : 렉서→파서→컴파일러
    - 런타임 : 가상머신
- 프레임 → run메서드 포문에서 함수를 실행할때 해당함수에 대한 프레임을 가져와서 명령어들을 실행함.
- 07 함수 → 아래 코드가 컴파일되고 가상머신에서 실행되는 동작과정 설명

```go
input: `
			let oneArg = fn(a){a};
			oneArg(24);
			`,
			expectedConstants: []interface{}{
				[]code.Instructions{
					code.Make(code.OpGetLocal, 0),
					code.Make(code.OpReturnValue),
				},
				24,
			},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 0),
				code.Make(code.OpSetGlobal, 0),
				code.Make(code.OpGetGlobal, 0),
				code.Make(code.OpConstant, 1),
				code.Make(code.OpCall, 1),
				code.Make(code.OpPop),
			},
```

- 08 내장함수 →아래코드가 컴파일되고 가상머신에서 실행되는 동작과정 설명

```go
>> let array = [1,2,3];
[1, 2, 3]
>> len(array)
3
```
