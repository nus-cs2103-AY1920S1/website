{% from "common/macros.njk" import embed_topic, thumb with context %}
{% from "schedule/index.md" import show_week_pagetop, show_project_summary with context%}
{{ show_week_pagetop(2, "project") }}

{{ show_project_summary(ip_file="ip-w02.md") }}

We'll be starting the individual project (iP) this week.

#### {{ thumb(0) }} Learn about the project

**Read the following two sections**, if you haven't done so already:

<div class="indented">

{{ embed_topic("../../admin/ip-overview.md#main", "Admin " + icon_embedding + " **iP - Overview**", "ipW02-overview", "3") }}
{{ embed_topic("../../admin/ip-grading.md#main", "Admin " + icon_embedding + " **iP - Grading**", "ipW02-overview", "1") }}
</div>

<include src="../../admin/ip-w02.md#body" />
