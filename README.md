raml2client
===========

RAML to ObjC, Java, JavaScript client.

```yaml
#%RAML 0.8
title: BookStore API
version: v1
baseUri: https://api.example.com/{version}
/books:
  get:
    description: Get all Books.
    responses:
      200:
        body:
          application/json:
            schema: !include schemas/books.json
  /{id}:
    get:
      description: Get a Book.
      responses:
        200:
          body:
            application/json:
              schema: !include schemas/book.json
```

To

```objc
@interface BookStoreAPI

- (RMCall *)listBook:(void(^)(NSArray /* BSBook */ *books))success (void(^)(NSError *error))failure;
- (RMCall *)getBook:(NSString *)identifier success:(void(^)(BSBook *book))success failure:(void(^)(NSError *error))failure;

@end
```

```java
interface BookStoreApi {
    List<Book> listBook();
    Book getBook(String id);
}
```
