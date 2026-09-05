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
   MAIN RESEARCH SECTIONS
   Talks, Posters, Research Visits, etc.
   ========================================== */

.publications h2.bibliography:not(.bibliography-year),
.publications h3.bibliography:not(.bibliography-year) {
  color: var(--global-text-color);
  font-weight: 400;
  font-size: 1.6rem;
  margin-top: 2.8rem;
  margin-bottom: 1.2rem;
  padding-bottom: 0.4rem;
  border-bottom: 1px solid var(--global-divider-color);
}

/* ==========================================
   YEARS: 2026, 2025, 2024...
   ========================================== */

.publications .bibliography-year {
  color: var(--global-text-color) !important;
  font-size: 1.8rem !important;
  font-weight: 400 !important;
  line-height: 1.25 !important;
  margin-top: 1.7rem !important;
  margin-bottom: 1rem !important;
  padding-bottom: 0 !important;
  border-bottom: none !important;
}


/* ==========================================
   RESEARCH STATISTICS
   ========================================== */

.research-stats {
  display: flex;
  justify-content: center;
  gap: 3.5rem;
  flex-wrap: wrap;
  margin: 2rem 0 3rem 0;
  text-align: center;
}

.research-stat {
  min-width: 110px;
  padding: 0.7rem 1rem;
  border-radius: 10px;
  transition:
    transform 0.2s ease,
    background-color 0.2s ease;
}

.research-stat:hover {
  transform: translateY(-3px);
  background-color: rgba(0, 118, 223, 0.06);
}

.research-stat-number {
  display: block;
  color: #0076df;
  font-size: 2.2rem;
  font-weight: 400;
  line-height: 1;
  margin-bottom: 0.4rem;
}

.research-stat-label {
  font-size: 0.9rem;
  color: var(--global-text-color);
}


/* ==========================================
   COLOURED LABELS
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

/* MSc / BSc Thesis */
.publications .abbr abbr.abbr-thesis {
  background-color: #5c6570 !important;
  color: white !important;
}
</style>


<div class="research-stats">

  <div class="research-stat">
    <span class="research-stat-number" id="talk-count">0</span>
    <span class="research-stat-label">Talks</span>
  </div>

  <div class="research-stat">
    <span class="research-stat-number" id="poster-count">0</span>
    <span class="research-stat-label">Posters</span>
  </div>

  <div class="research-stat">
    <span class="research-stat-number" id="visit-count">0</span>
    <span class="research-stat-label">Research Visits</span>
  </div>

</div>


<div class="publications">

{% bibliography %}

</div>


<script>
document.addEventListener("DOMContentLoaded", function () {

  /* ==========================================
     DETECT YEARS
     ========================================== */

  document
    .querySelectorAll(".publications .bibliography")
    .forEach(function (heading) {
      const text = heading.textContent.trim();

      if (/^(19|20)\d{2}$/.test(text)) {
        heading.classList.add("bibliography-year");
      }
    });


  /* ==========================================
     COLOUR LABELS AUTOMATICALLY
     ========================================== */

  document
    .querySelectorAll(".publications .abbr abbr")
    .forEach(function (label) {

      const text = label.textContent
        .trim()
        .toLowerCase();

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


  /* ==========================================
     COUNT ENTRIES IN A RESEARCH SECTION
     ========================================== */

  function countEntries(sectionNames) {

    const headings = document.querySelectorAll(
      ".publications h2.bibliography, .publications h3.bibliography"
    );

    for (const heading of headings) {

      const headingText = heading.textContent
        .trim()
        .toLowerCase();

      const isCorrectSection = sectionNames.some(function (name) {
        return headingText === name.toLowerCase();
      });

      if (!isCorrectSection) {
        continue;
      }

      let count = 0;
      let element = heading.nextElementSibling;

      while (element) {

        if (
          element.matches &&
          element.matches("h2.bibliography")
        ) {
          break;
        }

        if (
          element.matches &&
          element.matches("li")
        ) {
          count += 1;
        }

        if (element.querySelectorAll) {
          count += element.querySelectorAll("li").length;
        }

        element = element.nextElementSibling;
      }

      return count;
    }

    return 0;
  }


  /* ==========================================
     UPDATE THE NUMBERS
     ========================================== */

  const talks = countEntries([
    "Talks"
  ]);

  const posters = countEntries([
    "Posters"
  ]);

  const visits = countEntries([
    "Research Visits & Programs",
    "Research Stays & Programs",
    "Research Visits",
    "Research Stays"
  ]);


  document.getElementById("talk-count").textContent = talks;
  document.getElementById("poster-count").textContent = posters;
  document.getElementById("visit-count").textContent = visits;

});
</script>
