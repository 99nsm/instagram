[instagram_ppt.pdf](https://github.com/user-attachments/files/16157139/instagram_ppt.pdf)[instagram_ppt.pdf](https://github.com/user-attachments/files/16157137/instagram_ppt.pdf)![header](https://capsule-render.vercel.app/api?type=wave&color=auto&height=300&section=header&text=Hello&fontSize=90&animation=fadeIn&fontAlignY=38&desc=KyungMo's%20GitHub%20Profile&descAlignY=51&descAlign=62)


#  Team_project : Instagram
---
## 💻 프로젝트 소개
instagram 리모델링
---
## 📆 개발기간
+ 2024.06.28 ~ 07.04(7일) 

## 👫 맡은 역활
+ 나상미(프론트엔드 및 백엔드 총괄) : 모든페이지 구현, 백엔드 검토 및 오류 수정


## 📝 개발언어
<div style="display:flex; flex-direction:column; align-items:flex-start;">
    <!-- Backend -->
    <p><strong>Backend</strong></p>
    <div>
        <img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=Java&logoColor=white"> 
        <img src="https://img.shields.io/badge/spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"> 
    </div>
    <!-- Database -->
    <p><strong>Database</strong></p>
    <div>
        <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> 
    </div>
    <!-- Server -->
    <p><strong>Server</strong></p>
    <div>
        <img src="https://img.shields.io/badge/apache tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black">
    </div>
    <!-- Frontend -->
    <p><strong>Frontend</strong></p>
    <div>
        <img src="https://img.shields.io/badge/html5-E34F26?style=flat-square&logo=html5&logoColor=white"> 
        <img src="https://img.shields.io/badge/css-1572B6?style=flat-square&logo=css3&logoColor=white"> 
        <img src="https://img.shields.io/badge/javascript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"> 
    </div>
</div>

## ⚙ 개발환경
+ Java 11 version
+ JDK 11.0.22 version
+ Tomcat 9.088 version
+ Framework : Spring
+ Database : MySql(8.0.36)
+ ORM : Mybatis
---
## 📌 주요기능
+ 회원가입 페이지 : 아이디, 비밀번호, 이름, 성별 값 받기 및 유효성 검사
+ 로그인 페이지 : 로그인기능
+ pw찾기 페이지 : pw 변경 기능
+ 메인 페이지 : 현재 로그인한 사용자가 팔로워 하는 사용자 게시글 노출
+ 서치 페이지 : 사용자가 검색하고 싶은 다른 사용자 검색
+ 상세 페이지 : 사용자 프로필 사진 등 팔로우 및 게시글 관련 정보 노출
+ 게시물 만들기 페이지 : 게시글 작성 기능
+ 마이 페이지 : 현재 로그인한 사용자 정보 변경 가능


## 📎기타 자료 
[instagram_ppt.pdf](https://github.com/user-attachments/files/16157134/instagram_ppt.pdf)


데이터 베이스 생성 및 테이블 생성 쿼리문
create database instagram;

use instagram;

create table user_info (
                           U_seqno int auto_increment,
                           user_id varchar(50) not null unique,
                           user_pw varchar(50) not null,
                           user_name varchar(50) not null,
                           ph_num varchar(50) not null,
                           gender int(10) not null,
                           user_desc varchar(255),
                           user_photo varchar(255),

                           primary key(U_seqno)
);

create table follow (
                        F_seqno int auto_increment,
                        follower_id varchar(255) not null,
                        following_id varchar(255) not null,

                        primary key(F_seqno)
);

create table article (
                         A_seqno int auto_increment,
                         A_writer varchar(255) not null,
                         A_contents varchar(255) not null,
                         A_img varchar(255),
                         A_reg_date datetime default now(),
                         A_userPhoto varchar(255),
                         A_Heart int default 0,
                         A_comment int default 0,

                         primary key(A_seqno)
);

create table heart (
                       H_seqno int auto_increment,
                       FK_A_seqno int not null,
                       H_writer varchar(255) not null,

                       primary key(H_seqno)
);

create table comment (
                         C_seqno int auto_increment,
                         FK_A_seqno int not null,
                         C_writer varchar(255) not null,
                         C_txt varchar(255) not null,
                         C_reg_date datetime default now(),
                         C_class int(10) not null,
                         C_group_num int(10) not null,
                         C_order int(10) not null,

                         primary key(C_seqno)
);

직접 수정해야할 코드
** MypageController, ArticleController 에 있는 이미지 업로드하고 다운받는 경로 수정해야합니다
ex) private static final String F_PATH = "C:/Users/나상민/OneDrive/바탕 화면/tp_instagram/instagram/src/main/webapp/resources/img/";
