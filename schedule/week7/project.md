{% from "schedule/index.md" import show_week_pagetop, show_project_summary with context%}
{{ show_week_pagetop(7, "project") }}

{{ show_project_summary(ip_file="ip-w07.md", tp_file="project-w07-v11.md", milestone="v1.1") }}

# iP

<include src="../../admin/ip-w07.md#body" />

<br>
{{ hr_double }}

# tP: v1.1

<include src="../../admin/project-w07-v11.md#body" />