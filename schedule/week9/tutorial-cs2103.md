{% from "common/macros.njk" import embed_topic, thumb, show_as_tab, timing_badge with context %}
{% from "schedule/index.md" import show_week_pagetop with context%}
{{ show_week_pagetop(9, "tutorial") }}

#### {{ thumb(1) }} Demo v1.2

<div class="indented-level2">

{{ embed_topic("../../admin/project-w09-v12.md#demo", "Admin " + icon_embedding + " tP v1.2: Demo", "t9-demo", "3") }}
</div>

#### {{ thumb(2) }} Do a Postmortem of v1.2

* Share with the tutor your opinion on **how v1.2 went**, and your **plans to improve the process** (not the product) in v1.3, individually and as a team.

#### {{ thumb(3) }} Exercise: OODMs, Activity Diagrams

<div class="indented">

**3A.** {{ timing_badge("10-12 minutes", "info") }} Divide into two sub-teams and do the following questions on the whiteboard.<br>

<div class="indented">

**Sub-team 1:** %%{{ icon_tip }} You can use the _association class_ notation in the answer.%%
<include src="../../book/modeling/modelingStructures/objectOrientedDomainModels/q-courseDomainModel.md" />
<p/>

**Sub-team 2:**
<include src="../../book/modeling/modelingBehaviors/activityDiagrams/q-modelWorkflowOfBurgerShop.md" />
<p/>
</div>

**3B.** {{ timing_badge("5 minutes", "info") }} Familiarize yourself with the question the other sub-team worked on.

**3C.** [Group activity] Review the other sub-team's answer.
</div>

