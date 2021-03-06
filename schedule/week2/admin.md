{% from "schedule/index.md" import show_week_pagetop with context%}
{% from "common/macros.njk" import embed_topic, show_admin_sections_to_read, show_as_tab, thumb, timing_badge with context %}
{% from "common/admin.njk" import topics, policies, faqs, admin_topics_to_read, show_admin_summary with context %}

{{ show_week_pagetop(2, "admin") }}

{% call show_admin_summary() %}
1. Submit post-lecture quiz {{ timing_badge("by Thursday 2359") }}
1. Get connected with communication channels
{% endcall %}

<div id="additional">

#### {{ thumb(1) }} Submit post-lecture quiz {{ timing_badge("by Thursday 2359", "secondary") }}

* **Read weekly topics** allocated for this week. **Submit the `Lecture 1 - Post-Lecture Quiz`** (on LumiNUS) to test your knowledge of those topics.


#### {{ thumb(2) }} Get connected with communication channels

* Follow the 'Preparation' instructions of the following tools to get connected with the communication channels used by the module.

<div class="indented-level2">
{{ embed_topic("../../admin/tools.md#communication", "Admin " + icon_embedding + " **Tools - Communication**", "-", "3") }}
</div>

</div>

{{ show_admin_sections_to_read(topics, policies, faqs, admin_topics_to_read.week2, is_flat=false ) }}
