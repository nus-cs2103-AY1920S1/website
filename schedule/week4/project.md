{% from "schedule/index.md" import show_week_pagetop, show_project_summary with context%}
{{ show_week_pagetop(4, "project") }}

{{ show_project_summary(ip_file="ip-w04.md", tp_file="project-w04-inception.md") }}

# iP

<include src="../../admin/ip-w04.md#body" />

<br>
{{ hr_double }}

# tP: Inception

<include src="../../admin/project-w04-inception.md#body" />