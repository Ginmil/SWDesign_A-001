```mermaid
classDiagram
    class BankUI {

    }

    class User {
        - id : String
        - pw : String
        - name : String
        - phone : String
        - address : String
        + registerUser(id: String, pw: String, name: String, phone: String, address: String) boolean
        + updateUser(id: String, pw: String, name: String, phone: String, address: String) boolean
        + deleteUser(id: String) boolean
        + searchUser(id: String) boolean
    }

    class Account {
        - number : String
        - balance : long
        + deposit(id: String, amount: double) long
        + withdraw(id: String, amount: double) long
        + transfer(id: String, toAccountNumber: String, amount: double) long
        + computeBalance(userid: String) long
    }

    %% 관계 설정
    BankUI ..> Account : 의존
    Account "1..*" --> "1" User : 사용자조회
