# Thymeleaf

## Security
### [thymeleaf-extras-springsecurity](https://github.com/thymeleaf/thymeleaf-extras-springsecurity)
```html
<div th:if="${#authorization.expression('hasRole(''ROLE_ADMIN'')')}">
  This will only be displayed if authenticated user has role ROLE_ADMIN.
</div>
```

