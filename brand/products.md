# Products & Facts — Centennial Family Dentistry

Single source of truth for every practice fact used on the redesign pitch site.
All facts below are verbatim from the evidence captured in
`brand/_sources/2026-07-22/` on 2026-07-22. Tasks downstream of this file pull
facts ONLY from here.

Formatting contract: every fact is a `- ` bullet whose last element is its
`(source: <URL>, captured 2026-07-22)` citation. Prose lines (like this one)
carry no facts. Verify with:
`grep -nE '^- ' brand/products.md | grep -v 'source:'` → expected zero output.

## Locked Terminology & Fact Gotchas

**Never improvise practice facts.** If a fact isn't in this file, ask — do not fill
the gap from general knowledge. When a correction happens, it becomes a numbered
rule here the same session.

1. **The source site contradicts itself on price in six places. Do NOT pick a
   winner, do NOT average, do NOT quietly drop one figure.** Both figures are
   real and verbatim. Every contradicted service below is recorded twice in
   "Services & pricing," once per source page, each with its own citation. If a
   pitch page needs a single number for a contradicted service, that is a
   question for the practice — not a judgment call for a later session.
2. **Periodic Exam — $85 vs $76.** `/services-and-pricing` says "Periodic Exam:
   $85"; `/routine-cleanings-and-exams` says "Periodic Exam: $76".
3. **Cleaning — $145 vs $139.** `/services-and-pricing` says "Cleaning: $145";
   `/routine-cleanings-and-exams` says "Cleaning: $139".
4. **Fillings — $270-520 vs $212-416.** `/services-and-pricing` says "Fillings:
   $270-520"; both `/fillings-and-crowns` and `/cosmetic-dentistry` say
   "Fillings: $212-416".
5. **Crowns — $1,980 vs $1,828.** `/services-and-pricing` says "Crowns: $1,980";
   `/fillings-and-crowns` says "Crowns: $1,828".
6. **Botox — $14 per unit vs $13 per unit.** `/botox` and `/services-and-pricing`
   say "Botox: $14 per unit"; the TMJ page `/copy-of-fillings-and-crowns` says
   "Botox: $13 per unit" (for muscle-related TMJ issues). The two pages do not
   state that these are different products or different contexts of purchase —
   that reading would be an inference, so it is not made here.
7. **Invisalign — $3,000-5,400 vs $5,400.** `/cosmetic-dentistry` quotes a range,
   "Invisalign: $3,000-5,400"; the dedicated Invisalign page
   `/copy-of-fillings-and-crowns-2` quotes a flat "Invisalign: $5,400".
8. **All six of these contradictions must eventually be surfaced to the
   practice** — they are live, public, patient-facing inconsistencies on the
   practice's own site, and no pitch page should quote a single figure for a
   contradicted service until the practice resolves it. (They are also directly
   usable as evidence for the pitch's "your facts drift across pages" narrative,
   but that is a pitch decision, not a fact.)
9. **The "duplicate" pages are not duplicates.** Sleep Apnea has two source pages
   (`/blank-page` = in-office screening process, no price;
   `/copy-of-fillings-and-crowns-1` = patient-facing offer, with prices) and
   Botox has two (`/blank-page-1` = short paragraph, no price; `/botox` = fuller
   copy, with prices). The facts below are the UNION of each pair. Never source
   a merged service from just one of its two pages.
10. **A service with no listed price gets no price.** Where the source site lists
    no price, this file says "no price listed on source site." Do NOT write
    "call for pricing" for those — the only call-for-pricing language anywhere on
    the site is the single verbatim line on `/services-and-pricing` recorded
    below, and it applies to "all other treatment inquiries," not to any named
    service.
11. **Doctor names and credentials are exact as written.** "Dr. Eve Rutherford
    DDS", "Dr. Rachel Greene DDS", "Dr. Samiksha Gulrajani DMD" (homepage
    phrasing). The About page separately writes Dr. Greene's name as "Dr. Rachel
    (Krell) Greene" — that maiden-name parenthetical appears only in her bio.
    Dr. Rutherford is referred to on the routine-care page as "Dr. Eve".
12. **All review quotes are transcribed from images of text, not from page text.**
    The review widget renders each review as a 1080×1080 image with the words
    baked in as pixels. Quotes contain genuine typos and grammatical oddities
    ("with with regards", "then there", "the bestest"). Reproduce them EXACTLY —
    do not correct, tidy, or re-punctuate. Each quote's citation is the source
    image URL it was read from.
13. **The site's own displayed review count (13) is wrong.** There are 12 unique
    reviews; the widget pads to 13 by repeating the "Ed S" review as two separate
    image assets. Never write "13 reviews."
14. **Practice name is "Centennial Family Dentistry"** — never "Centennial
    Dentistry" (a patient uses that short form inside one review quote; that is
    inside a quote, not the practice's name) and never "Centennial Family
    Dental" (that string appears only in the Google search URL behind the
    reviews page's "Read More" link).
15. **No star rating exists in the evidence.** No card, page, or capture states a
    numeric rating, review date, or platform label. Do not put "4.9 stars" or a
    star row on any pitch page.
16. **Marne's title is written lowercase-m on the source site**: "Practice
    Business manager". Recorded verbatim; if the pitch site title-cases it, that
    is a copy-editing decision to make deliberately, not a fact correction.

## Practice identity

- Practice name: Centennial Family Dentistry (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Homepage H1: "Centennial Family Dentistry" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Homepage sub-line under the H1: "The Office of Dr. Eve Rutherford DDS, Dr. Rachel Greene DDS, and Dr. Samiksha Gulrajani DMD" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Page title (meta): "Home | Centennial Family Dentistry Snohomish" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Meta description, used verbatim as the site's own self-description: "Centennial Family Dentistry. We are a Snohomish dentist here to provide a dental home focused on prevention, education, compassion and meticulous dental care" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Site footer copyright line: "©2025 by Centennial Family Dentistry. Proudly created with Wix.com" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- About page heading: "Meet Our Team" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- No tagline or slogan distinct from the meta description appears anywhere in the captured evidence — not stated on the source site (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)

### Doctors (credentials exactly as written)

- Dr. Eve Rutherford, listed role "Dentist"; homepage credential "Dr. Eve Rutherford DDS" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Eve Rutherford is a graduate of the University of Washington School of Dentistry and received a Bachelor of Arts with Honors in Biology "form" Scripps College in Claremont, California (typo "form" is verbatim on the source page) (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Eve Rutherford worked in the Department of Pathology at the University of Washington studying connective tissue disorders prior to dental school; raised in Kalispell, Montana; graduated from Flathead High School (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Eve Rutherford has served on the Board of Directors for Washington Dental Service Foundation since 2015; in 2016 served on a task force with Washington State Health Care Authority seeking to improve benefits for Adult Dental Medicaid; is active with the ABCD Program (Access to Baby and Child Dentistry); and is Affiliate Faculty for the University of Washington Department of Pediatric Dentistry (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- "Dr. Rutherford practices Mondays, Tuesdays, Wednesdays, and Thursdays." (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Rachel Greene, listed role "Dentist"; homepage credential "Dr. Rachel Greene DDS"; bio name written "Dr. Rachel (Krell) Greene" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Rachel Greene is a graduate of the University of Michigan School of Dentistry and received a Bachelor of Arts with Honors in Science, Technology and Society from the University of Puget Sound (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Rachel Greene was born and raised in Snohomish and returned to her hometown to practice (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Rachel Greene is a professor at the University of Washington School of Dentistry, working as Clinical Director of Western Washington for the Service Learning Program and as a Clinical Instructor in the student patient clinic (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- "Dr. Greene practices on Thursdays and Fridays by appointment." (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Samiksha Gulrajani, listed role "Dentist"; homepage credential "Dr. Samiksha Gulrajani DMD" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Samiksha Gulrajani is originally from Cincinnati, Ohio; completed undergraduate studies in Mathematics and Neuroscience at the University of Pittsburgh, graduating with honors, with a minor in Chemistry; earned her Doctor of Dental Medicine (DMD) at the University of Pittsburgh School of Dental Medicine (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Dr. Samiksha Gulrajani completed a residency in Advanced Education in General Dentistry (AEGD), treating complex cases at the University and at a local urgent care clinic, and "specializes in providing comprehensive dental care, with a particular focus on patients with special needs" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- "Dr. Gulrajani practices on Monday, Tuesday, and Wednesday" (no trailing period on the source page) (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)

### Team (names and titles exactly as written)

- Brooke — Dental Hygienist; with the office since 2018; graduated from Lake Washington in 2014; "bring 10 years of experience" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Savannah — Dental Hygienist; earned her bachelor's degree from Seattle Central in 2016; part of the Centennial team since 2021; born and raised in Kirkland (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Juliana — Dental Hygienist; Bachelor of Science in Biology from Nova Southeastern University; graduated from Indian River State College in 2013 with a degree in Dental Hygiene; originally from Florida (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Becca — Dental Hygienist; her entire bio on the source site reads "Details coming soon!" and her photo slot uses the practice logo as a placeholder (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Amaya — Dental Assistant; graduated the West Coast College of Dental Assisting in 2022 (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Jessica — Dental Assistant; joined Centennial in 2021 with over 15 years of experience; works with Invisalign patients, who are seen "every 6 weeks for their Invisalign check ins"; originally from San Jose, moved to Washington in 2018 (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Kadi — Dental Assistant; joined Centennial in 2024 after graduating from West Coast College of Dental Assisting (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Yana — Scheduling Coordinator; started with the office in 2024; comes from a medical office; helps run Kids' Days and designs letters and flyers for the office (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Ciara — Scheduling Coordinator; joined the team in 2024 with 6 years of scheduling and insurance billing expertise; native to Washington state, grew up in Lake Stevens (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Kayleen — Scheduling Coordinator; joined the team in 2025 with 8 years of experience building trusting relationships; background in personal banking; native to Washington state, grew up in Lake Stevens (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Molly — Financial Coordinator; joined Centennial in 2023 with three years of experience in dental billing; also holds a Dental Assisting license (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Marne — "Practice Business manager" (lowercase m verbatim); no dates, credentials, or education stated in her bio (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Team size as published: 3 doctors + 12 staff members = 15 people listed on the About page (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)

## Contact & location

- Address: "133 Maple Ave Snohomish WA 98290" (verbatim, no commas on the source site) (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Phone: 360-568-6017, written on the homepage as "Phone: 360-568-6017" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Phone link target used in nav and on service pages: `tel:360-568-6017` / `tel:3605686017` (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Fax: "Fax: 360-568-9331" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Email: info@cfdentistrysnohomish.com (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Instagram: https://www.instagram.com/cfdentistrysnoho/ (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Facebook: https://www.facebook.com/CFDsnohomish/ (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Homepage social heading: "Check us out on our socials!" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Online bill pay — homepage section heading "Online Bill Pay", link label "Pay Here", destination https://bestcardteam.com/Payments/?Profile=centennialfamPAY (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Current site domain: https://www.cfdentistrysnohomish.com (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Employment section copy: "We strive to employ hard-working, dedicated and passionate employees. Every employee plays an integral part in delivering the best possible care to our patients. We highly value each and every one of our staff members. We're always looking for great people!" with a "Send us your resume!" mailto to info@cfdentistrysnohomish.com (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- No embedded map, no directions/parking text, no suite number, and no separate mailing address appear anywhere in the captured evidence — not stated on the source site (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)

## Hours of operation

Verbatim from the homepage "Hours of Operation" block, including its inconsistent
day-name abbreviations and the missing "am/pm" on Thursday — reproduce exactly if
quoting the current site; any normalization is a redesign decision, not a fact.

- Section heading: "Hours of Operation" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Mon: 7:30am-4:00pm" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Tues: 8:00am-4:30pm" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Wednesday: 7:30am-5:00pm" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Thursday: 7:30-4:00pm" (no "am" on the opening time — verbatim) (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Friday: By Appointment Only" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- "Saturday & Sunday: Closed" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- No holiday hours, emergency after-hours instructions, or lunch-closure times appear in the captured evidence — not stated on the source site (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)

## Services & pricing

Group names and anchor IDs below are locked by `brand/_sources/2026-07-22/service-inventory.md`
(Task 2) and must not be renamed downstream. Prices are verbatim, including the
source site's own inconsistent formatting (`$270-520` with a hyphen, `$14 per unit`).

### The practice-wide price list page (`/services-and-pricing`)

This is the site's own consolidated price list. Several of its figures conflict
with the same service's price on its dedicated page — see gotcha rules 2–7.

- Page H1: "Prices for Service" (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "New Patient Exam, Cleaning, and imaging: $456" (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Comprehensive Exam: $139" (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Periodic Exam: $85" — CONFLICTS with $76 on the routine-care page, see gotcha 2 (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Emergency Exam: $125" (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Cleaning: $145" — CONFLICTS with $139 on the routine-care page, see gotcha 3 (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Fillings: $270-520" — CONFLICTS with $212-416 on two other pages, see gotcha 4 (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Crowns: $1,980" — CONFLICTS with $1,828 on the fillings-and-crowns page, see gotcha 5 (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Extractions: $285-440" — this is the only page in the evidence that prices extractions; there is no dedicated extractions page (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Custom Bleach Trays: $350" — same figure as "Custom Trays: $350" on the whitening page, different label (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- "Botox: $14 per unit" — CONFLICTS with $13 per unit on the TMJ page, see gotcha 6 (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- Closing line, verbatim including the site's literal asterisks: "\*\*For all other treatment inquiries please call our office at 360-568-6017\*\*" — this is the ONLY call-for-pricing language on the site (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- The page ends with a link labeled "Click here to see our Financing Options" pointing to /financing (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)

### Routine care (`#routine-care`)

- Page H1: "Routine Cleanings and Exams"; subhead: "The Care You Deserve" (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- Body copy, para 1: "To keep your teeth looking and feeling great, visit your dentist every six months. During your initial visit, Dr. Eve, Dr. Greene or Dr. Gulrajani typically take X-rays of your teeth to assess the structure and health of your teeth, gums and jaw. They also ask about your dental history and home-care habits to get a full picture of your oral care needs." (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- Body copy, para 2: "Routine checkups involve removing tartar buildup from your teeth, polishing surfaces with a fluoride paste and testing each tooth's strength and health. Your hygienist will also give you a personal oral hygiene consultation, teaching you the skills you need to prevent tooth decay and gum disease at home." (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- "Comprehensive Exam: $139" — agrees with the price-list page (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- "Periodic Exam: $76" — CONFLICTS with $85 on the price-list page, see gotcha 2 (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- "Cleaning: $139" — CONFLICTS with $145 on the price-list page, see gotcha 3 (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- Page CTA label: "Get in Touch" linking to tel:3605686017 (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)

### Restorative (`#restorative`)

- Page H1: "Fillings and Crowns"; subhead: "Helping You Get Healthy" (source: https://www.cfdentistrysnohomish.com/fillings-and-crowns, captured 2026-07-22)
- Body copy, verbatim and written in the FIRST PERSON SINGULAR despite the practice having three dentists: "Through a holistic approach to medicine, I try viewing each patient as a whole rather than a single symptom to be treated. This is just one of many procedures I perform when coming up with any diagnosis. Your health deserves proper care and attention and I'm able to provide. Please contact me today to schedule an appointment." (source: https://www.cfdentistrysnohomish.com/fillings-and-crowns, captured 2026-07-22)
- "Fillings: $212-416" — CONFLICTS with $270-520 on the price-list page, see gotcha 4 (source: https://www.cfdentistrysnohomish.com/fillings-and-crowns, captured 2026-07-22)
- "Crowns: $1,828" — CONFLICTS with $1,980 on the price-list page, see gotcha 5 (source: https://www.cfdentistrysnohomish.com/fillings-and-crowns, captured 2026-07-22)
- Extractions are priced only on the price-list page ("Extractions: $285-440"); there is no restorative page describing extractions — not stated on the source site beyond that one line (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)

### Cosmetic (`#cosmetic`)

#### Cosmetic Dentistry (overview page)

- Page H1: "Cosmetic Dentistry"; subhead: "Taking Care of You" (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- Body copy: "Beyond aesthetics, cosmetic dentistry is a journey to renewed self-confidence and holistic well-being. We offer teeth-colored fillings, whitening, veneers, Invisalign and more. Call today to see how we can improve your smile!" (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- Veneers are named in that copy as an offered service but are never priced or described on any captured page — no price listed on source site (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- "Fillings: $212-416" — same figure as the fillings-and-crowns page; CONFLICTS with the price-list page, see gotcha 4 (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- "Whitening: $90-600" — a range; the dedicated whitening page breaks this into four separately-priced options below (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- "Invisalign: $3,000-5,400" — CONFLICTS with the flat $5,400 on the dedicated Invisalign page, see gotcha 7 (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- This page carries an unattributed patient testimonial at the bottom whose text is identical to the "Kay" review on the reviews page: "I have been going to Centennial Family Dentistry for many years. I've had standard cleanings and some major dental repairs and can't imagine going anywhere else. Doctors, hygienists and staff are wonderful!" — the page itself gives no name (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)

#### Invisalign

- Page H1: "Invisalign"; subhead: "Helping You Get Healthy" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-2, captured 2026-07-22)
- Body copy: "Unlike traditional braces, Invisalign is a clear aligner therapy designed to help teens and adults achieve beautifully aligned smiles. Whether you're preparing for a big event, boosting your confidence, or just tired of crooked teeth, Invisalign offers a subtle, stress-free solution. We are here to guide you through every step of the process." (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-2, captured 2026-07-22)
- "Invisalign: $5,400" — CONFLICTS with the $3,000-5,400 range on the cosmetic-dentistry page, see gotcha 7 (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-2, captured 2026-07-22)
- Invisalign patients are seen "every 6 weeks for their Invisalign check ins" per the dental assistant Jessica's bio (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)

#### Teeth Whitening

- Page H1 is "Whitening" although the nav label for this page is "Teeth Whitening"; subhead: "Helping You Get Healthy" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- Body copy: "Our professional teeth whitening solutions are tailored to your goals and lifestyle, whether you're looking for dramatic results in a single visit, or a gradual lift from home." (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Zoom in office whitening is a two-hour appointment using a light-activated gel to lift deep stains quickly. Great for special events or anyone wanting quick results!" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Opalescence Take Home Whitening Syringes work with custom trays to deliver professional-grade whitening at home" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Opalescence Go Trays are a convenient option with no impressions or trays needed. They are prefilled and ready to use." (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Zoom: $600" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Take Home Syringes: $45 for 2-pack" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Custom Trays: $350" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)
- "Go Trays: $90 for 10-pack" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-4, captured 2026-07-22)

#### Botox and Fillers

This service has TWO source pages carrying different facts — the union of both is
below. See gotcha 9. Both pages share the same on-page H1, "Botox and Fillers,"
even though the nav labels them "Botox and Fillers" and "Botox" separately.

- Page H1 on both source pages: "Botox and Fillers"; the `/botox` page adds the subhead "Taking Care of You" (source: https://www.cfdentistrysnohomish.com/botox, captured 2026-07-22)
- Body copy (page A, `/blank-page-1`), complete: "We offer botox and fillers to all of our current and new patients. You do not have to be a dental patient in order to schedule these services. We offer both medical and cosmetic botox. Call our office today to schedule an appointment or consult." (source: https://www.cfdentistrysnohomish.com/blank-page-1, captured 2026-07-22)
- Page A (`/blank-page-1`) lists no prices at all — no price listed on source site for that page (source: https://www.cfdentistrysnohomish.com/blank-page-1, captured 2026-07-22)
- Body copy (page B, `/botox`): "We offer Botox treatments as part of our comprehensive approach to dental and facial wellness. Whether you're seeking relief from jaw tension or looking to smooth fine lines, Botox is a safe, effective solution. You do not have to be a dental patient in order to schedule these services." (source: https://www.cfdentistrysnohomish.com/botox, captured 2026-07-22)
- "Botox: $14 per unit" — CONFLICTS with $13 per unit on the TMJ page, see gotcha 6 (source: https://www.cfdentistrysnohomish.com/botox, captured 2026-07-22)
- "Filler: $650 per syringe" — priced only on this page; no other page in the evidence prices filler (source: https://www.cfdentistrysnohomish.com/botox, captured 2026-07-22)
- Only page A states that both medical and cosmetic botox are offered; only page B states the dental-and-facial-wellness framing and carries pricing — a merged section needs both (source: https://www.cfdentistrysnohomish.com/blank-page-1, captured 2026-07-22)
- Neither Botox page names a specific product brand, states unit counts for a typical treatment, or names the filler product — not stated on the source site (source: https://www.cfdentistrysnohomish.com/botox, captured 2026-07-22)

### Sleep & TMJ (`#sleep-tmj`)

#### Sleep Apnea

This service also has TWO source pages carrying different facts — union below.
See gotcha 9.

- Page H1 on both source pages: "Sleep Apnea"; page A (`/blank-page`) adds the line "Do you think you have Sleep Apnea?" and the H2 "Sleep Apnea Screening in Our Office"; page B (`/copy-of-fillings-and-crowns-1`) adds the subhead "Helping You Sleep Better" (source: https://www.cfdentistrysnohomish.com/blank-page, captured 2026-07-22)
- Body copy (page A, `/blank-page`), complete: "In our office we take pride in not only making sure our patients have great oral health, we make sure they have good overall health as well. During each dental exam, our doctors look for signs that you could have sleep apnea such as a small airway. This is usually followed up by a series of questions that can help determine if you are a good candidate for an at home sleep study. This is something that is offered in our office and is usually much cheaper and more comfortable than an "in lab" sleep study. From there if you are a good candidate for an oral sleep appliance, that is something we can make in our office. You can also check out our blog post as well as call our office for more questions regarding sleep apnea. 360-568-6017" (source: https://www.cfdentistrysnohomish.com/blank-page, captured 2026-07-22)
- Page A (`/blank-page`) lists no prices at all — no price listed on source site for that page (source: https://www.cfdentistrysnohomish.com/blank-page, captured 2026-07-22)
- Body copy (page B, `/copy-of-fillings-and-crowns-1`): "If you struggle with loud snoring, restless nights,or feeling tired even after a full night's sleep, you may be dealing with sleep apnea. We offer simple, effective solutions to help you breathe and sleep better. We work closely with medical professionals to ensure an accurate diagnosis and treatment. Whether you're newly diagnosed or looking for CPAP alternatives, our team is here to help!" (missing space after "nights," is verbatim) (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-1, captured 2026-07-22)
- Page B offer list, verbatim: "At Home Sleep Testing to help you in the comfort of your own home." and "Custom Oral Sleep Appliances to gently reposition your jaw to keep your airway open during sleep." (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-1, captured 2026-07-22)
- "Home Sleep Tests: $250" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-1, captured 2026-07-22)
- "Oral Sleep Device: $2,500" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns-1, captured 2026-07-22)
- Only page A describes the in-exam screening protocol (small-airway checks, follow-up questions, at-home study candidacy, in-office appliance fabrication) and the "cheaper and more comfortable than an in lab sleep study" claim; only page B carries pricing and the CPAP-alternative framing — a merged section needs both (source: https://www.cfdentistrysnohomish.com/blank-page, captured 2026-07-22)
- Page A refers to "our blog post" about sleep apnea; the blog is out of scope for this project and was not captured, so its content is unknown (source: https://www.cfdentistrysnohomish.com/blank-page, captured 2026-07-22)

#### TMJ

- Page H1: "TMJ"; subhead: "Helping You Get Relief from TMJ" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- Body copy, verbatim including the "being"-for-"bring" typo and the hyphen-for-dash: "If you're experiencing jaw soreness, clicking or popping, facial pain or frequent headaches, you may be suffering from TMJ disorder-also known as TMD. We offer advanced diagnostics and customized treatment options to being you long-lasting relief. We are here to help find custom solutions that work!" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- Offer list, verbatim: "CBCT Imaging to get a clear, 3D view of your jaw joint, allowing us to pinpoint the cause of your discomfort." (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- Offer list, verbatim: "Occlusal Orthotic Devices to align your bite and relieve pressure on your jaw joint" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- Offer list, verbatim: "Botox for muscle related TMJ issues to relax overactive jaw muscles" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- "CBCT: $550" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- "Orthotic: $1,268" (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)
- "Botox: $13 per unit" — CONFLICTS with $14 per unit on /botox and /services-and-pricing, see gotcha 6 (source: https://www.cfdentistrysnohomish.com/copy-of-fillings-and-crowns, captured 2026-07-22)

### Technology & extras (`#technology-extras`)

#### 3D Printing

- Page H1: "3D Printing"; subhead: "Taking Care of You" (source: https://www.cfdentistrysnohomish.com/3d-printing, captured 2026-07-22)
- Body copy: "Using the latest 3D printing technology, our office is now able to fabricate custom night guards, onlays, and more right here in-house. This means faster turnaround times, fewer appointments, and less hassle, all while maintaining the same high standards of fit, comfort, and durability. With digital scanning and printing, we can create restorations that are highly accurate and tailored specifically to your bite. 3D printing allows us to deliver reliable, high-quality solutions without the wait of traditional lab work." (source: https://www.cfdentistrysnohomish.com/3d-printing, captured 2026-07-22)
- No price listed on source site for 3D printing, night guards, or onlays (source: https://www.cfdentistrysnohomish.com/3d-printing, captured 2026-07-22)

#### Laser Dentistry

- Page H1: "Laser Dentistry"; subhead: "Improve Breathing, Sleep, and Oral Function Naturally" (source: https://www.cfdentistrysnohomish.com/laser, captured 2026-07-22)
- Body copy, complete: "We also offer laser frenectomy procedures using a gentle CO₂ laser for faster healing and minimal discomfort." (source: https://www.cfdentistrysnohomish.com/laser, captured 2026-07-22)
- "Lingual Frenectomy: $572" — the only price on the page (source: https://www.cfdentistrysnohomish.com/laser, captured 2026-07-22)
- The page prices only lingual frenectomy; no labial/buccal frenectomy or other laser procedure is named or priced — not stated on the source site (source: https://www.cfdentistrysnohomish.com/laser, captured 2026-07-22)

#### Willo Toothbrush

- Page H1: "Willo"; subhead: "Taking Care of You"; the homepage links to this page under the label "Willo Toothbrush" (source: https://www.cfdentistrysnohomish.com/willo, captured 2026-07-22)
- Body copy: "We're excited to offer the Willo toothbrush, an innovative, automated brushing system designed to take the guesswork out of daily oral care. Willo uses gentle, effective technology to clean all sides of your teeth at once, helping you achieve a thorough clean in less time than traditional brushing. Designed with comfort and consistency in mind, the Willo system supports better brushing habits and can be especially helpful for patients who struggle with technique or time. By incorporating Willo into your routine, you can enjoy a simpler, more efficient way to maintain a healthy smile at home." (source: https://www.cfdentistrysnohomish.com/willo, captured 2026-07-22)
- The page carries a "More Information" link to the practice's Willo partner page: https://partners.willo.com/CFDSNOHOMISH (source: https://www.cfdentistrysnohomish.com/willo, captured 2026-07-22)
- No price listed on source site for the Willo toothbrush (source: https://www.cfdentistrysnohomish.com/willo, captured 2026-07-22)

#### Kids' Days

- Page H1: "Kids' Days"; subhead: "Creating a comfortable environment" (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)
- Body copy: "A few times each month, we turn our office into a fun, kid-focused dental space just for Kids' Days! On these special days, we see only our younger patients and transform the office with playful themes, decorations, and activities to help kids feel comfortable and excited about visiting the dentist. From jungle adventures to outer space, each theme is designed to make dental care fun and approachable—while our team focuses on gentle, age-appropriate care. Whether it's your child's first dental visit or a regular check-up, Kids' Days are a great way to create positive dental experiences early on. Appointments fill quickly, so be sure to ask about our next Kids' Day when scheduling!" (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)
- Kids' Days frequency as stated: "A few times each month" — no specific dates, schedule, or booking mechanism is published (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)
- The page carries a 6-image photo gallery ("1/6") with themes including "hallo" and "hawaii"; the image asset URLs did not resolve in the capture and would need a fresh browser-based capture if the photos are wanted (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)
- Yana, Scheduling Coordinator, is the staff member credited with Kids' Days: "I love to make our Kids' Days fun for everyone, including the parents." (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- No price listed on source site for Kids' Days (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)

### Recurring service-page CTA

- Every service page except `/blank-page` and `/blank-page-1` ends with the same CTA label, "Get in Touch," linking to tel:3605686017 (source: https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams, captured 2026-07-22)
- Four service pages reuse the identical subhead "Taking Care of You" (Cosmetic Dentistry, Botox and Fillers, 3D Printing, Willo) and three reuse "Helping You Get Healthy" (Fillings and Crowns, Invisalign, Whitening) — template copy left unchanged from the site's Wix theme (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)

## Financing

Maps to the Services & Pricing page's `#financing` group per the Task-2 map.

- Page H1: "Financing Options" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Body copy, verbatim: "We believe quality dental care should be accessible and affordable for everyone. That's why we offer flexible financing options through CareCredit and Cherry, two trusted providers that let you split your treatment costs into manageable monthly payments. Whether you're planning a routine procedure or a more extensive treatment, financing can help you get the care you need without delay. Both options feature a quick application process, and approval decisions are often made within minutes. If you have questions or need help applying, our front desk team is always happy to walk you through the process and find the best solution for your budget." (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Two financing providers are offered, and only two: CareCredit and Cherry (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Type of Financing: "Healthcare credit card" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Approval Time: "Instant approval in most cases" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Payment Terms: "Short and long term options (6-60 months)" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Interest Options: "0% interest promotional periods available" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Credit Check: "Yes" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — Best For: "Larger treatment plans or ongoing care" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- CareCredit — apply link: https://www.carecredit.com/go/442XZT/ (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Type of Financing: "'Buy Now, Pay Later' plan" (curly double quotes in source) (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Approval Time: "Instant approval in most cases" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Payment Terms: "Flexible monthly payment plans (split up to 12 months)" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Interest Options: "0% APR options available based on credit" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Credit Check: "Soft credit check (no impact on score)" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — Best For: "Smaller procedures or one-time costs" (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- Cherry — apply link: https://tree.withcherry.com/centennial-family-dentistry (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- The comparison table's "Apply Here" row is empty in both columns on the source page; the two apply links sit below the table as plain links (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- The financing page says nothing about dental insurance — no insurers accepted, no in-network/out-of-network statement, no in-house membership plan appears anywhere in the captured evidence. Not stated on the source site (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)

## Reviews

All quotes below are transcribed from images of text — the practice's review
widget renders each review as a 1080×1080 image with the words baked in as
pixels, so no DOM text exists to copy. Each citation is the full-resolution
source image the quote was read from, so any quote can be re-verified. The Kay
and Tiffany transcriptions were independently verified against their source
images by the project lead; the remaining ten were transcribed the same way.
Typos and grammatical oddities in the quotes are the patients' own and are
reproduced exactly — see gotcha 12.

- Reviews live on the page titled "Check out our reviews" at /about-me (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)
- 12 unique reviews exist; the widget displays a count of "1/13" because the "Ed S" review appears twice as two separate image assets (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)
- Homepage review section heading: "See what our patients are saying:" (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- The reviews page's only outbound link is labeled "Read More" and points to a Google Search results page for "centennial family dental reviews" — the page never states which platform the reviews come from, so "Google reviews" is an inference and must not be printed as fact (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)
- Reviewer identification is first name only, or first name plus last initial (e.g. "Ed S", "F G") — no full names are published (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)
- No star ratings, review dates, or platform labels appear on any review card or anywhere on the reviews page — not stated on the source site (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)

### Verbatim quotes (transcribed from image)

- Kay: "I have been going to Centennial Family Dentistry for many years. I've had standard cleanings and some major dental repairs and can't imagine going anywhere else. Doctors, hygienists and staff are wonderful!" (transcribed from image; independently verified) (source: https://static.wixstatic.com/media/856d6c_f8a699b786684210ade3a46574cf5672~mv2.png, captured 2026-07-22)
- Tiffany: "This place felt like a full service concierge dental office. Out of the gate my hygienist acknowledged that the dentist is most people's least fave place and offers a blanket, pillow, etc and immediately helped to put my mind at ease and help me to relax. I can't express enough how incredibly thorough they are with up to date technology with their x-rays, full scans and incredible attention to detail with with regards to my overall health, not just my teeth. It's the most comprehensive dental exam I have ever had and my husband had the exact same experience at his first visit. We were both blown away and will be bringing our 5 year old here too. It's honestly the first time in my life I won't feel nervous to go back! Real talk!" (transcribed from image; independently verified; "with with regards" is verbatim) (source: https://static.wixstatic.com/media/856d6c_88e08e5df4fd44bc8bdd80dbc26bb188~mv2.png, captured 2026-07-22)
- Ed S: "They are great and I will never go any other place then there they were so good from the start to the finish." (transcribed from image; "then there" is verbatim) (source: https://static.wixstatic.com/media/856d6c_4d144440f2484318b530bcd3a019b6f5~mv2.png, captured 2026-07-22)
- Ashley: "Hands down the best dental experience I've ever had. The dental assistant and Dr. Greene were exceptional and made me feel so comfortable. What a cozy, homey dental office. I actually can't wait for my next appointment!" (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_1933063137044035bbf8e7bec2bfbba2~mv2.png, captured 2026-07-22)
- Nena: "I can't say how grateful I am to have such a wonderful dental office in my own town. I have had excellent dentists throughout my life, in my home state here and in NYC, and Centennial in Snohomish is at the top of that list. Drs. Rutherford and Greene and their staff are highly skillful and dedicated. They really look out for you, thinking long term, and doing work that's necessary at the time while keeping watch on potential problem spots. The hygienists are wonderful. I really feel cared for in every way, as a patient and as a senior. They are very community-minded and a valuable asset to our area. Thank you, everybody at Centennial!" (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_003600ad6cca41f4b478b482829b3827~mv2.png, captured 2026-07-22)
- Taylor: "This office is extremely kind and professional. They know how to make a dentist office an enjoyable experience! I had Invisalign done here as well, and they have been more than wonderful. I highly recommend them to anyone!" (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_2be432c8a54f486184bd626b55522ab9~mv2.png, captured 2026-07-22)
- Kailey: "I'll never go to another dentist again. Centennial Family Dentistry has been absolutely fantastic. I'm a chronic dentist-avoider due to dental anxiety, and didn't go to the dentist for seven years. I went here for the first time 1.5 years ago. I have been here enough times since then, that I was comfortable to get Invisalign treatment as well! A highly personable dentist with stellar care & customer service!" (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_9692d95ce8dc41de8b529e5aafbbd6a5~mv2.png, captured 2026-07-22)
- Meagan: "I highly recommend Centennial Family Dentistry to anyone who feels anxious about going to the dentist. The staff is incredibly patient and understanding, and they take the time to answer all of my questions. They've made me feel so comfortable that I've even recommended them to several friends and family members." (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_a36f56899cae45a5b86b324d82e4b28b~mv2.png, captured 2026-07-22)
- Bob: "The staff was very professional and knowledgeable. My hygienist did an awesome job cleaning my teeth and giving me educational tips and information." (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_349259592d1642cf90b064e0ec93af66~mv2.png, captured 2026-07-22)
- Yoni: "Dr. Gulrajani is the bestest." (transcribed from image; "bestest" is verbatim) (source: https://static.wixstatic.com/media/856d6c_3146485fb4ea4f4891dd164abb4b8a47~mv2.png, captured 2026-07-22)
- William: "I've been a patient at Centennial Family Dentistry since moving to Snohomish four years ago, and I couldn't be more pleased with my experience. The entire staff and doctors are genuinely caring, take the time to listen, and always make me feel welcome. Their friendly and professional approach has made every visit a positive one. I highly recommend Centennial Family Dentistry for anyone looking for exceptional dental care." (transcribed from image) (source: https://static.wixstatic.com/media/856d6c_842a10f33f9143b9904eff43d7b8ff3f~mv2.png, captured 2026-07-22)
- F G: "5 STARS for the team at Centennial Dentistry! I recently had an issue with a crown; I was fortunate enough to get scheduled quickly and Dr. Greene was able to help me with a temporary. Her assistant Jessica was great to work with and took extra steps to make sure the temporary was fitted and comfortable. Everybody at this office is friendly, nice and professional!" (transcribed from image; the shortened practice name "Centennial Dentistry" is the patient's own wording) (source: https://static.wixstatic.com/media/856d6c_c8ce8b37752140fa8fd349ffd367f0f1~mv2.png, captured 2026-07-22)
- Slide 13 of the widget repeats the "Ed S" quote verbatim from a second, distinct image asset — it is not a 13th review (source: https://static.wixstatic.com/media/856d6c_e2c9d8eb61514c88b60387cf71beda8d~mv2.png, captured 2026-07-22)

## Absent from the evidence

Recorded so a later session does not invent them. Each of these is a fact one
would reasonably expect a dental practice site to carry and which simply is not
present in any 2026-07-22 capture. Anything needed from this list requires a
question to the practice or a fresh capture — not a guess.

- Insurance accepted, in-network status, or an in-house membership plan — not stated on the source site (source: https://www.cfdentistrysnohomish.com/financing, captured 2026-07-22)
- New-patient forms, patient portal, or online appointment booking — no such link exists in the homepage link dump; scheduling is by phone only (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Emergency/after-hours contact instructions — the only emergency reference anywhere is the "Emergency Exam: $125" price line (source: https://www.cfdentistrysnohomish.com/services-and-pricing, captured 2026-07-22)
- Year the practice was founded, years in business, or practice history — not stated on the source site (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Patient volume, number of patients served, or any statistic of that kind — not stated on the source site (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Languages spoken, accessibility information, or parking details — not stated on the source site (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Becca's biography (Dental Hygienist) — the source site itself says only "Details coming soon!" (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Marne's start year, credentials, or education — not stated on the source site (source: https://www.cfdentistrysnohomish.com/about-us, captured 2026-07-22)
- Veneers, night guards, and onlays are named as offered but carry no description page and no price — no price listed on source site (source: https://www.cfdentistrysnohomish.com/cosmetic-dentistry, captured 2026-07-22)
- Blog content — the Blog is a live nav item but was excluded from scope and never captured, so nothing from it may be cited (source: https://www.cfdentistrysnohomish.com/, captured 2026-07-22)
- Kids' Days gallery photographs — the page's six gallery images did not resolve to real asset URLs in the capture and would need a fresh browser-based capture (source: https://www.cfdentistrysnohomish.com/kidsdays, captured 2026-07-22)
- A numeric review rating for a homepage trust badge — no rating exists in any capture; it would have to come from Google or Facebook directly (source: https://www.cfdentistrysnohomish.com/about-me, captured 2026-07-22)
