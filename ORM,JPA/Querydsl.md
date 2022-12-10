# QueryDsl 왜 써?

## QueryDsl이란?

- Query DSL은 오픈소스 프로젝트로 JPQL을 Java 코드로 작성할 수 있도록 하는 라이브러리다.

## QueryDsl이 필요한 이유

Jpa에는 쿼리 메서드 기능과 @Query를 통해서 많은 기능을 만들 수 있지만, 고정된 형태의 값을 가진다는 단점이 있다.
즉 간단한 로직을 작성하는데는 큰 문제는 없으나, 복잡한 로직의 경우엔 쿼리 문자열이 상당히 길어집니다.

jpql문자열에 오타 혹은 문법적인 오류가 존재하면 정적쿼리라면 어플리케이션 로딩 시점에 알 수 있으나 그 외에는 런타임 시점에서 에러가 난다.

---

위의 문제점들을 해소 할 수 있는 프레임워크가 바로 querydsl이다.

## 장점

1. 문자가 아닌 쿼리로 작성하기때문에 컴파일 시점에 오류를 찾기 비교적 쉽다.
2. 자동완성,IDE의 도움을 받을 수 있다.
3. 동적인 쿼리 작성이 편리함
4. 쿼리 작성 시 제약조건,메서드 등을 재사용을 할 수있다.

## 사용예제

```java
Article findByTitleContains(String title);
```

“제목에 특정 문자열이 포함된 기사를 조회”라는 간단한 조회는 JPA로 인터페이스에 메서드 명세만 잘 해주면 쉽게 할 수있다.

하지만 조금 복잡한 쿼리가 필요한 경우를 보면

```java
@Query(value = "SELECT id, title, user_id FROM article WHERE user_id IN (SELECT id FROM user WHERE level > :level)", nativeQuery = true)
List<Article> findByLevel(String level);
```

기사를 작성한 사용자의 레벨에 따른 조회 라는 쿼리는 JPA 자체 제공 메서드만으로 해결하기는 어렵기때문에 네이티브 쿼리를 고려해 볼 수 있다.  그렇다면 위에 네이티브 쿼리를 QueryDsl로 바꾸면 어떻게 될까?

```java
public List<Article> findByUserLevel(String level) {
    QArticle article = QArticle.article;
    QUser user = QUser.user;

    return queryFactory.selectFrom(article)
        .where(
            article.userId.in(
                JPAExpressions
                    .select(user.id)
                    .from(user)
                    .where(user.level.gt(level))
            )
        )
        .fetch();
}
```

네이티브 쿼리보다 가독성이 더 좋아진걸 볼 수 있다. 또한 다양한 조건들을 처리 할 수 있다.
