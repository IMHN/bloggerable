---
title: Comments link
description: Link to the comments on the post.
category: Snippets
subcategory: Posts
---

Link to the comments on the post.


## Default

```html
<!-- Number of comments -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <b:if cond='data:post.commentSource != 1'>
      <!-- Google+ Comments (No) -->
      <b:message name='messages.numberOfComments'>
        <b:param expr:value='data:post.numberOfComments' name='numComments'/>
      </b:message>
    <b:else/>
      <!-- Google+ Comments (Yes) -->
      <data:messages.comments/>
    </b:if>
  </a>
</b:if>
```


## Fallback

```html
<!-- Number of comments -->
<b:if cond='data:post.allowComments'>
  <a expr:href='data:post.commentsUrl' expr:title='data:messages.comments'>
    <b:attr name='b:whitespace' value='remove'/>
    <b:if cond='data:post.commentSource != 1'>
      <!-- Google+ Comments (No) -->
      <b:message name='messages.numberOfComments'>
        <b:param expr:value='data:post.numberOfComments' name='numComments'/>
      </b:message>
    <b:else/>
      <!-- Google+ Comments (Yes) -->
      <data:messages.comments/>
    </b:if>
  </a>
<b:else/><!-- fallback -->
  <span>Comments are disabled</span>
</b:if>
```
