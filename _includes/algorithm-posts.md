{%- comment -%}
  Lists the posts of one algorithm category, grouped by tag.
  Posts without a tag are listed last, under "태그 없음" when the category also has tagged posts.

  Parameters:
    category - second-level category name, e.g. "백준"
    empty    - text shown when the category has no posts
{%- endcomment -%}
{%- assign section_posts = site.categories[include.category] -%}
{%- if section_posts and section_posts.size > 0 -%}
  {%- assign tag_names = section_posts | map: "tags" | join: "|" | split: "|" | uniq | sort -%}
  {%- assign untagged = section_posts | where_exp: "post", "post.tags.size == 0" -%}
  {%- for tag in tag_names -%}
    {%- if tag == "" -%}{%- continue -%}{%- endif -%}
    {%- assign tagged = section_posts | where_exp: "post", "post.tags contains tag" %}

### {{ tag }}

<ul>
    {%- for post in tagged %}
<li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
    {%- endfor %}
</ul>
  {%- endfor -%}
  {%- if untagged.size > 0 -%}
    {%- if untagged.size < section_posts.size %}

### 태그 없음
    {%- endif %}

<ul>
    {%- for post in untagged %}
<li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
    {%- endfor %}
</ul>
  {%- endif -%}
{%- else %}

{{ include.empty }}
{%- endif %}
