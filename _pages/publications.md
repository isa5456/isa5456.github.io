---
layout: page
permalink: /publications/
title: Research
description: Research publications, talks, posters, research visits, and other research-related activities.
nav: true
nav_order: 1
---

<style>
/* ==========================================
   RESEARCH SECTIONS: Talks, Posters, etc.
   ========================================== */

<style>
/* Research sections: Talks, Posters, etc. */
.publications h2.bibliography {
  color: var(--global-text-color);
  font-weight: 700;
  font-size: 1.6rem;
  margin-top: 2.8rem;
  margin-bottom: 1.2rem;
  padding-bottom: 0.4rem;
  border-bottom: 1px solid var(--global-divider-color);
}

/* Years: make them look like normal h3 headings */
.publications h3.bibliography {
  color: var(--global-text-color) !important;
  font-size: 1.75rem !important;
  font-weight: 400 !important;
  line-height: 1.25 !important;
  margin-top: 1.6rem !important;
  margin-bottom: 1rem !important;
}
</style>

/* ==========================================
   LABELS
   ========================================== */

.publications .abbr abbr {
  border: none;
  font-weight: 500;
}

/* Seminar */
.publications .abbr abbr.abbr-seminar {
  background-color: #0076df !important;
  color: white !important;
}

/* Conference */
.publications .abbr abbr.abbr-conference {
  background-color: #2e7d32 !important;
  color: white !important;
}

/* Workshop */
.publications .abbr abbr.abbr-workshop {
  background-color: #d97706 !important;
  color: white !important;
}

/* Journal Club */
.publications .abbr abbr.abbr-journal-club {
  background-color: #c2415d !important;
  color: white !important;
}

/* Research Talk */
.publications .abbr abbr.abbr-research-talk {
  background-color: #0f766e !important;
  color: white !important;
}

/* Research Stay */
.publications .abbr abbr.abbr-research-stay {
  background-color: #52758c !important;
  color: white !important;
}

/* Program */
.publications .abbr abbr.abbr-program {
  background-color: #7656a8 !important;
  color: white !important;
}

/* MSc / BSc thesis */
.publications .abbr abbr.abbr-thesis {
  background-color: #5c6570 !important;
  color: white !important;
}
</style>

<div class="publications">

{% bibliography %}

</div>

<script>
document.addEventListener("DOMContentLoaded", function () {
  document.querySelectorAll(".publications .abbr abbr").forEach(function (label) {
    const text = label.textContent.trim().toLowerCase();

    if (text === "seminar") {
      label.classList.add("abbr-seminar");
    } else if (text === "conference") {
      label.classList.add("abbr-conference");
    } else if (text === "workshop") {
      label.classList.add("abbr-workshop");
    } else if (text === "journal club") {
      label.classList.add("abbr-journal-club");
    } else if (text === "research talk") {
      label.classList.add("abbr-research-talk");
    } else if (text === "research stay") {
      label.classList.add("abbr-research-stay");
    } else if (text === "program") {
      label.classList.add("abbr-program");
    } else if (text.includes("thesis")) {
      label.classList.add("abbr-thesis");
    }
  });
});
</script>
