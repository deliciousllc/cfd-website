# Rendered Reviews — Centennial Family Dentistry

Captured: 2026-07-22
Source page: https://www.cfdentistrysnohomish.com/about-me ("Check out our reviews")
Method: The page embeds a Wix image-gallery widget showing one review card at
a time (each card is a 1080x1080 image with the quote and reviewer name
baked in as text, styled with quote marks, in the site's serif display font
on white). A "1/13" counter confirms 13 total slide positions. `get_page_text`
and `read_page` cannot extract this content — it is pixel content inside an
image, not DOM text — so the inline carousel view was not usable directly
(images stayed in a permanent low-quality blur-up placeholder state in this
browser session and never sharpened).

What worked: clicking the image opened the widget's built-in fullscreen
lightbox (accessible buttons labeled "next"/"previous"/"close" were found via
`read_page` after the DOM tree was inspected — the gallery's arrow controls
live in a shadow-root component not reachable via plain `document.querySelector`).
In the lightbox, each slide rendered at full quality and legible. I paged
through with the "next" button (`computer` click on the accessibility-tree
ref, with a 2-6s wait for the crossfade transition to finish) and read each
slide directly from the screenshot — a legitimate transcription of real,
rendered, site-published content, not a fabrication.

I paged through all 13 slide positions. Slide 3 ("Ed S") and slide 13 turned
out to be the same review text verbatim — confirmed by continuing to click
past slide 13 and landing back on slide 1 ("Kay"), i.e. the widget's own
review data contains one duplicate entry, padding a true count of 12 unique
reviews to a displayed total of 13. This is a property of the practice's own
review widget, not a capture error.

## Reviews (verbatim transcriptions, in carousel order)

Each entry below is followed by its source image URL: the original,
full-resolution Wix media asset behind that carousel slide, with the Wix
transform parameters stripped (everything from `/v1/` onward removed),
so the exact image the quote was transcribed from can be reopened later
at no cost. See "Source image URL method" below for how these were
obtained and their confidence level.

1. **Kay**
   > I have been going to Centennial Family Dentistry for many years. I've had standard cleanings and some major dental repairs and can't imagine going anywhere else. Doctors, hygienists and staff are wonderful!
   Source image: https://static.wixstatic.com/media/856d6c_f8a699b786684210ade3a46574cf5672~mv2.png (independently verified against the source image)

2. **Tiffany**
   > This place felt like a full service concierge dental office. Out of the gate my hygienist acknowledged that the dentist is most people's least fave place and offers a blanket, pillow, etc and immediately helped to put my mind at ease and help me to relax. I can't express enough how incredibly thorough they are with up to date technology with their x-rays, full scans and incredible attention to detail with with regards to my overall health, not just my teeth. It's the most comprehensive dental exam I have ever had and my husband had the exact same experience at his first visit. We were both blown away and will be bringing our 5 year old here too. It's honestly the first time in my life I won't feel nervous to go back! Real talk!
   Source image: https://static.wixstatic.com/media/856d6c_88e08e5df4fd44bc8bdd80dbc26bb188~mv2.png

3. **Ed S**
   > They are great and I will never go any other place then there they were so good from the start to the finish.
   Source image: https://static.wixstatic.com/media/856d6c_4d144440f2484318b530bcd3a019b6f5~mv2.png

4. **Ashley**
   > Hands down the best dental experience I've ever had. The dental assistant and Dr. Greene were exceptional and made me feel so comfortable. What a cozy, homey dental office. I actually can't wait for my next appointment!
   Source image: https://static.wixstatic.com/media/856d6c_1933063137044035bbf8e7bec2bfbba2~mv2.png

5. **Nena**
   > I can't say how grateful I am to have such a wonderful dental office in my own town. I have had excellent dentists throughout my life, in my home state here and in NYC, and Centennial in Snohomish is at the top of that list. Drs. Rutherford and Greene and their staff are highly skillful and dedicated. They really look out for you, thinking long term, and doing work that's necessary at the time while keeping watch on potential problem spots. The hygienists are wonderful. I really feel cared for in every way, as a patient and as a senior. They are very community-minded and a valuable asset to our area. Thank you, everybody at Centennial!
   Source image: https://static.wixstatic.com/media/856d6c_003600ad6cca41f4b478b482829b3827~mv2.png

6. **Taylor**
   > This office is extremely kind and professional. They know how to make a dentist office an enjoyable experience! I had Invisalign done here as well, and they have been more than wonderful. I highly recommend them to anyone!
   Source image: https://static.wixstatic.com/media/856d6c_2be432c8a54f486184bd626b55522ab9~mv2.png

7. **Kailey**
   > I'll never go to another dentist again. Centennial Family Dentistry has been absolutely fantastic. I'm a chronic dentist-avoider due to dental anxiety, and didn't go to the dentist for seven years. I went here for the first time 1.5 years ago. I have been here enough times since then, that I was comfortable to get Invisalign treatment as well! A highly personable dentist with stellar care & customer service!
   Source image: https://static.wixstatic.com/media/856d6c_9692d95ce8dc41de8b529e5aafbbd6a5~mv2.png

8. **Meagan**
   > I highly recommend Centennial Family Dentistry to anyone who feels anxious about going to the dentist. The staff is incredibly patient and understanding, and they take the time to answer all of my questions. They've made me feel so comfortable that I've even recommended them to several friends and family members.
   Source image: https://static.wixstatic.com/media/856d6c_a36f56899cae45a5b86b324d82e4b28b~mv2.png

9. **Bob**
   > The staff was very professional and knowledgeable. My hygienist did an awesome job cleaning my teeth and giving me educational tips and information.
   Source image: https://static.wixstatic.com/media/856d6c_349259592d1642cf90b064e0ec93af66~mv2.png

10. **Yoni**
    > Dr. Gulrajani is the bestest.
    Source image: https://static.wixstatic.com/media/856d6c_3146485fb4ea4f4891dd164abb4b8a47~mv2.png

11. **William**
    > I've been a patient at Centennial Family Dentistry since moving to Snohomish four years ago, and I couldn't be more pleased with my experience. The entire staff and doctors are genuinely caring, take the time to listen, and always make me feel welcome. Their friendly and professional approach has made every visit a positive one. I highly recommend Centennial Family Dentistry for anyone looking for exceptional dental care.
    Source image: https://static.wixstatic.com/media/856d6c_842a10f33f9143b9904eff43d7b8ff3f~mv2.png

12. **F G**
    > 5 STARS for the team at Centennial Dentistry! I recently had an issue with a crown; I was fortunate enough to get scheduled quickly and Dr. Greene was able to help me with a temporary. Her assistant Jessica was great to work with and took extra steps to make sure the temporary was fitted and comfortable. Everybody at this office is friendly, nice and professional!
    Source image: https://static.wixstatic.com/media/856d6c_c8ce8b37752140fa8fd349ffd367f0f1~mv2.png

13. **(duplicate of #3, "Ed S")** — confirmed by continuing past this slide and cycling back to "Kay" (slide 1).
    Source image: https://static.wixstatic.com/media/856d6c_e2c9d8eb61514c88b60387cf71beda8d~mv2.png (a distinct media asset from slide 3's, despite carrying the same review text — the practice's widget exported two separate image files with identical wording)

13/13 source image URLs obtained. None are missing.

## Source image URL method

Re-visited `https://www.cfdentistrysnohomish.com/about-me` in the browser
tools on 2026-07-22 specifically to collect these URLs (separate visit from
the original transcription pass). The inline carousel only renders one
image at a time and this session's lightbox click did not visibly render
past the low-quality blur-up placeholder (the same rendering limitation
noted in the original transcription pass above), so URLs were not read off
a legible on-screen image this time. Instead they were read directly from
the gallery widget's own DOM data: each of the 13 slides is backed by a
`[data-testid="gallery-item-click-action-image-zoom"]` element whose
`aria-describedby` attribute is `describedby_item-N-comp-mdf352ds` for
N = 0..12, in the same left-to-right document order as the carousel's
"1/13" position counter, and each carries an `<img>` (at minimum a 49x49
blurred placeholder, at most a full 918x956 render) pointing at that
slide's real Wix media asset — the underlying media ID is identical
regardless of which transform size loaded, so even the two slides that
had only loaded their blurred thumbnail (items 10 and 11, i.e. slides 11
and 12) still yielded a correct, usable full-resolution URL once the Wix
transform parameters were stripped.

Confidence: slide 1 ("Kay", item index 0) matches the URL independently
confirmed by the coordinator
(`856d6c_f8a699b786684210ade3a46574cf5672~mv2.png`), which cross-validates
that this DOM index order matches display order. Slides 2–13 rely on that
same index-order mapping (not independently re-confirmed slide-by-slide
against a legible on-screen image in this session) — this is "reading the
gallery component's data" as suggested, not a guess, but flagged here as a
slightly lower-confidence method than the direct visual transcription used
for the review text itself.

## What is NOT available

- No star ratings are shown on the review cards themselves or anywhere on
  this page — only quote + first name/initial. If a numeric star rating is
  needed for a homepage badge (e.g. "4.9 stars"), it isn't sourced from this
  page and would need to come from Google/Facebook directly, which is out of
  scope for this capture-only task.
- No review dates are shown.
- No platform attribution is shown on the cards (no "via Google" or "via
  Facebook" label); the page's "Read More" link points to a Google Search
  results page for "centennial family dental reviews", implying these are
  sourced from Google reviews, but that is an inference, not a stated fact
  on the page — flagged as such, not presented as confirmed.
- Reviewer full names are not shown — only first name, or first name + last
  initial (e.g. "Ed S", "F G").
