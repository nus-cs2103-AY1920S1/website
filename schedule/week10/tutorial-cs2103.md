{% from "common/macros.njk" import embed_topic, thumb, show_as_tab, timing_badge with context %}
{% from "schedule/studentData.njk" import team_review_allocation with context %}
{% from "schedule/index.md" import show_week_pagetop with context%}
{{ show_week_pagetop(10, "tutorial") }}

#### {{ thumb(0) }} Smoke-test CATcher

<div class="indented-level2">

<box dismissible>

%%**{{ icon_info }} Some background:** As you know, our <tooltip content="i.e., Practical Exam">PE</tooltip> includes peer-testing tP products under exam conditions. In the past, we used GitHub as the platform for that -- which was not optimal (e.g., it was hard to ensure the compulsory labels have been applied). As a remedy, some ex-students have been developing an app called <tooltip content="CAT stands for Crowd-sourced Anonymous Testing">CATcher</tooltip> that we would like to use for the PE this semester.%%
</box>

In this tutorial, we would like to smoke-test the CATcher app **to ensure it can run in your computer**.
<p/>

<panel type="info" header="**The steps for smoke-testing CATcher:**" minimized>

1. **Download the latest version** of the CATcher executable from [https://github.com/CATcher-org/CATcher/releases](https://github.com/CATcher-org/CATcher/releases).
1. **Launch the app.** Allow the app to run if there are security warnings %%(e.g., for Win 10, click the `More Info` link in the security warning and choose `Run anyway`)%%.<br>
   {{ icon_tip }} If the app is blocked by your virus scanner, put it in a new folder and add the folder to the _exclusions_ list of the virus scanner.
1. **Login**: Choose the profile `CS2103/T Alpha Test`, enter your GitHub credentials, and submit.<br>
   {{ icon_tip }} If you have 2FA enabled for GitHub, you can [create a personal access token with `repo` permissions](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) and use that as the password.<br>
   <img src="../../admin/images/catcherLogin.png" />
1. **Let CATcher create a repo named `alpha`** in your GitHub account, when it asks for permission. That repo will be used to hold the bug reports you will create in this testing session.
1. **Use the app to create 1-2 dummy bug reports**, similar to how you would enter bug reports in the GitHub issue tracker. e.g., you can copy-paste screenshots into the bug description and use Markdown syntax.<br>
  {{ icon_info }} The `severity` and `type` labels are compulsory.
1. **Report any problems you encounter** at the [CATcher issue tracker](https://github.com/CATcher-org/CATcher/issues).


</panel>
<p/>

{{ icon_important_big_red }} **Being able to run CATcher is important for the PE** -- if you are unable to run it, please follow up via the [CATcher issue tracker](https://github.com/CATcher-org/CATcher/issues) until you resolve the issue ASAP.

</div>

#### {{ thumb(1) }} Review the <tooltip content="Developer Guide">DG</tooltip> of a Peer Team

* **Divide into two sub-teams**, ensuring that each team has at least one member who is good with UML.
* **Find the team your sub-team have been allocated to discuss** in the panel below and click on the link to locate their team PR.

{% macro get_review_allocation_for_team(reviewing_team) -%}
{%- set reviewed_team = "" -%}
{% for allocation in team_review_allocation  -%}
{% if allocation[0] == reviewing_team %}{% set reviewed_team %}{{ allocation[1] }}{% endset %}{% endif %}
{%- endfor %}{{ reviewed_team }}
{%- endmacro %}

{% macro get_pr_link(team_id) -%}
[{{ team_id }}](https://github.com/nus-{{ module | lower}}-{{ semester }}/addressbook-level3/pulls?q=is%3Aopen+is%3Apr+label%3Atutorial.{{ team_id.slice(0, -2) }}+label%3Ateam.{{ team_id.slice(-1) }})
{%- endmacro  %}

<div class="indented-level2">

<panel header="Allocation for DG review" >

Team          | Sub-team A <small>%%(backup)%%</small> | Sub-team B <small>%%(backup)%%</small>
--------------|----------------------------------------|---------------------------------------
{% for team in team_review_allocation  %}
{%- set backup_team1 %}{{ get_review_allocation_for_team(team[1]) }}{% endset -%}
{%- set backup_team2 %}{{ get_review_allocation_for_team(team[2]) }}{% endset -%}
{{ team[0] }} | {{ get_pr_link(team[1]) }} <small>%%({{ get_pr_link(backup_team1) }})%%</small> | {{ get_pr_link(team[2]) }} <small>%%({{ get_pr_link(backup_team2) }})%%</small>
{% endfor %}
</panel>
</div>

* **Go to the PR** and **navigate the to the <trigger trigger="click" for="modal:t10-netlifyPreview">Netlify preview</trigger>**.
* **Confirm that the DG has significant updates**, to the diagrams in particular. If it doesn't, you can review the _backup_ team (given within brackets). %%If even the backup team is not suitable, ask the tutor for a suggestion or choose any random teams having tutorials in the same day.%%
* **Evaluate the `Design` and the `Implementation` sections against the stated expectations** (given further down); add your observations as comments.<br>

<modal large title="How to access the Netlify preview" id="modal:t10-netlifyPreview">
  <img src="../../admin/images/prNetlifyPreview.png" />
</modal>

<div class="indented-level2">

<box>

* To be done collectively with sub-team members.
* Add _review comments_ in the corresponding place of the code. But ==if the <tooltip content="i.e., the tab named `Files changed`">_diff view_</tooltip> is too laggy, you can use a normal comment==. 
* Choose the `Start a review` option rather than `Add single comment`.
* Each person can do their own review, but coordinate with sub-team members to avoid duplicating the same point.
* Phrase your comments as question/doubts (e.g., `Is this format correct? Should it be ... instead?`) rather than directives (e.g., `Change this to ...`).
* Where possible, use screenshots from their DG in your comments, preferably with annotations. This is particularly useful when commenting on diagrams.
* Do not finalize the review at this stage. Just keep adding comments.
* <span class="text-success">**The understanding you gain from this exercise can indirectly determine how well you do in your own project.**</span> ==If you have even the slightest doubt about your observations in this exercise, please discuss it with the tutor== to ensure you have the right understanding of the criteria used.
</box>

<box border-left-color="green">

##### <span class="text-success">DG Expectations</span> 
{{ icon_important_big_red }} Pay attention to these as they are same as the final evaluation criteria of the DG.<br>

Also see:
{{ embed_topic("../../admin/project-w10-mid-v13.md#dgTips", "Admin " + icon_embedding + " tP: mid-v1.3 → DG Tips", "t10-dgTips", "3") }}

**Architecture**
- [ ] The Architecture diagram uses intuitive symbols.
- [ ] No indiscriminate use of double-headed arrows.
- [ ] Any <tooltip content="e.g., the sequence diagram showing interactions between main components">_architecture-level_</tooltip> diagrams do not contain lower-level details.
- [ ] The description given is understandable and sufficiently high-level.

**Diagrams**
- [ ] Uses the correct UML notation.<br>
  &nbsp;&nbsp;{{ icon_info }} If you notice UML notation errors, please point them out.
- [ ] Not cluttered with too much unnecessary details.
- [ ] Each diagrams is relatively simple and easy to understand.
- [ ] Uses multiple types of diagrams (ideal: uses Class Diagrams, Object Diagrams, Sequence Diagrams, Activity Diagrams)
- [ ] Diagrams are well-integrated into the description.
- [ ] Not repetitive (opposite: many similar diagrams with minor differences).

**Descriptions**
- [ ] Easy to understand/follow (==were you able to understand their design?==)
- [ ] Just enough information: Not too much information. All important information is given.

**Overall**
- [ ] Polished: The document looks neat, well-formatted, and professional.<br>
  &nbsp;&nbsp;{{ icon_info }} e.g., Are the diagrams resized to match the text size of the main document?

</box>

</div>

* **Discuss your comments/observations/doubts with the tutor** and other team members to confirm the comments you entered are correct.
* **Update your review comments if necessary**, based on the discussion you just had. After that, you can submit the review.<br>


