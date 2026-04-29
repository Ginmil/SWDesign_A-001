```mermaid
graph LR
    %% Actor 정의
    User((온라인 뱅킹 사용자))
    BankSystem["<<System>>\n외부 은행 시스템"]

    subgraph Online_Banking_System [온라인 뱅킹 시스템]
        %% 사용자 관리 유스케이스
        UC1(사용자 등록)
        UC2(사용자 수정)
        UC3(사용자 삭제)
        UC4(사용자 조회)

        %% 계좌/금융 유스케이스
        UC5(입금)
        UC6(출금)
        UC7(이체)
        UC8(잔액 조회)

        %% 포함 관계 (Include) - 사용자 관리
        UC1 -. "&lt;&lt;include&&gt;&gt;" .-> UC4
        UC2 -. "&lt;&lt;include&&gt;&gt;" .-> UC4
        UC3 -. "&lt;&lt;include&&gt;&gt;" .-> UC4

        %% 포함 관계 (Include) - 금융 거래
        UC5 -. "&lt;&lt;include&&gt;&gt;" .-> UC4
        UC5 -. "&lt;&lt;include&&gt;&gt;" .-> UC8
        
        UC6 -. "&lt;&lt;include&&gt;&gt;" .-> UC4
        UC6 -. "&lt;&lt;include&&gt;&gt;" .-> UC8
        
        UC7 -. "&lt;&lt;include&&gt;&gt;" .-> UC4
        UC7 -. "&lt;&lt;include&&gt;&gt;" .-> UC8
    end

    %% 사용자 연결
    User --> UC1
    User --> UC2
    User --> UC3
    User --> UC4
    User --> UC5
    User --> UC6
    User --> UC7
    User --> UC8

    %% 외부 시스템 연결 (금융 거래는 외부 은행 시스템과 연동)
    UC5 --- BankSystem
    UC6 --- BankSystem
    UC7 --- BankSystem
