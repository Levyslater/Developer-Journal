

### Date:

2025-08-09

### Topic / Discovery:

A One-to-Many relationship in Django is represented by a **ForeignKey** on the "many" side.

### Code Snippet:

```python
class BlogPost(models.Model):
    title = models.CharField(max_length=255)

class Comment(models.Model):
    blog_post = models.ForeignKey(
        BlogPost,
        on_delete=models.CASCADE,
        related_name='comments'
    )
    content = models.TextField()
```

### How I Discovered It:

While exploring relationships between `BlogPost` and `Comment`, I noticed that the "one" side (`BlogPost`) doesn’t explicitly declare the relationship — instead, the "many" side (`Comment`) stores the `ForeignKey`.

### Why It Matters:

This helps avoid redundancy. The reverse access (`blogpost.comments.all()`) comes from the `related_name`, which Django generates automatically if not explicitly set.

### Questions / Next Steps:

* Test reverse lookup without setting `related_name`.
* Explore `OneToOneField` to compare its behavior with `ForeignKey`.

