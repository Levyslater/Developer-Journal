

### Date:
2025-08-09

### Topic / Discovery:
ManyToMany relationships in Django don’t store a ForeignKey on either model.

### Code Snippet:
```python
class BlogPost(models.Model):
    title = models.CharField(max_length=255)
    tags = models.ManyToManyField('Tag', related_name='blog_posts')
How I Discovered It:
During a conversation about BlogPost ↔ Tag relationships, I realized Django creates a hidden “through” table instead of storing a FK on either model.

Why It Matters:
Understanding this prevents wrong assumptions when writing queries and helps when designing schemas, especially for performance optimization.

Questions / Next Steps:
Try defining a custom through model with extra fields.

Compare query performance for ManyToMany vs ForeignKey joins.
