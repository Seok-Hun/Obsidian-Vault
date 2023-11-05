# 목적
### [[Database Transaction | Transaction]]에 의해 데이터가 변경될 경우 변경 전의 DataBase Image를 저장하는데 사용
### Transaction rollback, 읽기 일관성 유지(Read consistency), Transaction recovery를 위해 존재
> [!Note]
> ### Transaction recovery
> Transaction recovery는 transaction이 진행되는 동안 오류 발생 시 database가 다시 열릴 때 commit 되지 않은 사항은 rollback 한다. 이 때, rollback segment가 사용된다.

> [!Note]
> ### Undo
> Undo와 Rollback은 기본적으로 동의어이다. 따라서 undo segment와 rollback segment는 같은 의미이다.