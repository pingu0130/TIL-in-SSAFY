#SQLD 정리
###20221022
---
1. CONSTRAINT (제약조건)
- 결점없이 정확하고 유효한 데이터가 데이터베이스에 저장될 수 있도록 하기 위하여 데이터베이스를 조작하는데 한계를 규정한 것이다. 사용자가 원하는 데이터만 걸러내도록 조건을 만드는 것을 제약조건을 건다라고 한다.
```sql
 CONSTRAINT 제약 ID 제약내용(컬럼명); 
 ```
2. Delete(/Modify) Action
- Casecade : Master삭제 시 Child 같이 삭제
- Set Null : Master 삭제 시 Child 해당 필드 Null
- Set Default : Master 삭제 시 Child 해당 필드 Default값으로 설정
- Restrict : Child 테이블에 PK값이 없는 경우만 Master 삭제 허용
- No Action : 참조무결성을 위반하는 삭제/수정 액션을 취하지 않음

3. SQLD에서는 여러객의 컬럼을 동시에 수정하는 구문은 지원하지 않는다.

4. Insert Action
- Automatic : Master 테이블에 PK가 없는 경우 Master PK를 생성 후 Child 입력
- Set Null : Master 테이블에 PK가 없는 경우 Child 외부키를 Null 값으로 처리
- Set Default : Master 테이블에 PK가 없는 경우 Child 외부키를 지정된 기본값으로 입력
- Dependent : Master 테이블에 PK가 존재할때만 Child입력 허용
- No Action : 참조무결성을 위반하는 입력 액션을 취하지 않음

