```mermaid
classDiagram
    class 사용자 {
        - id : String
        - 암호 : String
        - 성명 : String
        + 사용자등록(id : String, 암호 : String, 성명 : String) boolean
        + 사용자수정(id : String, 암호 : String, 성명 : String) boolean
        + 사용자삭제(id : String) boolean
        + 사용자id조회(id : String) boolean
    }

    class 도서 {
        - 도서id : String
        - 도서명 : String
        - 출판사 : String
        - 대여상태 : boolean
        + 도서등록(도서id : String, 도서명 : String, 출판사 : String) boolean
        + 도서수정(도서id : String, 도서명 : String, 출판사 : String) boolean
        + 도서삭제(도서id : String) boolean
        + 도서id조회(도서id : String) boolean
        + 대여상태확인(도서id : String) boolean
    }

    class 대여정보 {
        - 대여id : String
        - id : String
        - 도서id : String
        - 대여일 : int
        - 반납예정일 : int
        - 반납일 : int
        + 대여(id : String, 도서id : String) String
        + 반납(id : String, 도서id : String) String
        + 연체확인(반납예정일 : int, 반납일 : int) boolean
    }

    %% DB 구조를 반영한 실선(연관 관계)
    대여정보 "0..*" --> "1" 사용자 : 대여주체
    대여정보 "0..*" --> "1" 도서 : 대여대상