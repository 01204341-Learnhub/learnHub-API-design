# LearnHub API design

## Auth API

```
├── auth(/auth)
│   ├── login (/auth/login)
│   ├── signup (/auth/signup)
```

## User API

mainly used for displaying user's information such as profile, achievements, programs taken etc. adding, editing or removing programs need to be done via programs API

```
├── users(/users)
│   ├── students(/users/students) -get
│   │   ├── student(/users/students/{student-id}) -get,patch,delete
│   │   │   ├── achivements(/users/students/{student-id}/achivements) -get
│   │   │   ├── programs(/users/students/{student-id}/programs) -get
│   │   │   │   ├── classes(/users/students/{student-id}/programs/classes) -get
│   │   │   │   ├── courses(/users/students/{student-id}/programs/courses) -get
│   │   │   ├── wishlist(/users/students/{student-id}/wishlist) -get,post
│   │   │   │   ├── wishlist-item(/users/students/{student-id}/wishlist/{wishlist-item-id}) -get,delete
│   │   │   ├── config(/users/students/{student-id}/config) -get,patch
│   │   │   ├── payment-methods(/users/students/{student-id}/payment-methods) -get,post
│   │   │   │   ├── payment-method(/users/students/{student-id}/payment-methods/{payment-method-id}) -get,patch,delete
│   │   │   ├── purchases-history(/users/students/{student-id}/purchases-history) -get
│   │   │   ├── basket(/users/students/{student-id}/basket) -get,post
│   │   │   │   ├── basket-item(/users/students/{student-id}/basket/{basket-item-id}) -delete
│   ├── teachers(/users/teachers) -get
│   │   ├── teacher(/users/teachers/{teacher-id}) -get,patch,delete
│   │   │   ├── programs(/users/teachers/{teacher-id}/programs) -get
│   │   │   │   ├── classes(/users/teachers/{teacher-id}/programs/classes) -get
│   │   │   │   ├── courses(/users/teachers/{teacher-id}/programs/courses) -get
│   │   │   ├── config(/users/teachers/{teacher-id}/config) -get, patch
│   │   │   ├── payment-methods(/users/teachers/{teacher-id}/payment-methods) -get,post
│   │   │   │   ├── payment-method(/users/teachers/{teacher-id}/payment-methods/{payment-method-id}) -get,patch,delete
│   │   │   ├── earnings(/users/teachers/{teacher-id}/earnings) -get
```

## Achievement API

Use to create, edit and condition achievements.

**For future developments. Right now we hardcode. XD**

```
├── achievements(/achievements)
```

## Program API

Use for both stores and learning pages

**note : transaction API handles student enrollments.**

```
├── programs(/programs) -get
│   ├── courses(/programs/courses) -get,post
│   │   ├── course(/programs/courses/{course-id}) -get,patch,delete
│   │   │   ├── students(/programs/courses/{course-id}/students) -get
│   │   │   ├── chapters(/programs/courses/{course-id}/chapters) -get,post
│   │   │   │   ├── chapter(/programs/courses/{course-id}/chapters/{chapter-id}) -get,patch,delete
│   │   │   │   │   ├── lessons(/programs/courses/{course-id}/chapters/{chapter-d}/lessons) -get,post
│   │   │   │   │   │   ├── lesson(/programs/courses/{course-id}/chapters/{chapters-id}lessons/{lesson-id}) -get,patch,delete
│   │   │   ├── announcements(/programs/courses/{course-id}/announcements) -get,post
│   │   │   │   ├── announcement(/programs/courses/{course-id}/announcements/{announcement-id}) -get,patch,delete
│   ├── classes(/programs/classes) -get,post,patch,delete
│   │   ├── class(/programs/classes/{class-id}) -get,patch,delete
│   │   │   ├── students(/programs/classes/{class-id}/students) -get
│   │   │   ├── threads(/programs/classes/{class-id}/threads) -get,post
│   │   │   │   ├── post(/programs/classes/{class-id}/threads/{thread-id}) -get,post
```

## Quiz API

Use for quiz.

```
├── quizzes(/quizzes) -get,post
│   ├── quiz(/quizzes/{quiz_id}?student_id=123) -get,patch
│   │   ├── result(/quizzes/{quiz_id}/result?student_id=123) -get,post
```

## Transaction API

Use for transactions

```
├── transaction(/transaction)
│   ├── enroll(/transaction/enroll) -post
│   ├── cashout(/transaction/cashout) -post
```
