# First Sunday, church data sources

All facts in `churches.json` came from each church's own website only. No Yelp, no
Google reviews, no blog roundups, no denominational directories were used for any
vibe claim (music, dress, size, kids). Denominational directories and general web
search were used only to locate the correct official URL for a church, never as
the source of a fact.

Every church was read on **2026-08-15**. Where a fact is not listed for a church
below, it was not stated on that church's site and is recorded as `null` in
`churches.json`, not guessed.

**Size, researched then removed (2026-08-15):** two research passes
re-crawled every church's own site (about, history, staff, leadership,
annual report, and giving pages, not just the homepage and visit page)
looking specifically for a real attendance or membership number. Only
**one** church stated one directly: Faith Church Orlando's own "About" page
says it serves "over 5,000 people... each Sunday." Blessed Trinity Catholic
Church's site states 1,955 registered families in a fundraising update, but
that is a registered-household count, not a weekly headcount, converting
"families registered" into "people at a Sunday Mass" would have been exactly
the kind of inference this dataset exists to avoid, so it was never counted.
The other 18 churches had nothing more specific than vague aspirational
language ("small but mighty," "thousands of families" as a vision
statement). With a real answer for 1 of 20 churches, `sizeBand` was checked
against `PERSONA.md` and removed as a quiz axis entirely, see
`DESIGN.md` section 10 for the replacement. This field no longer exists in
`churches.json`.

**Meeting space and language, added in its place (2026-08-15):** a third
research pass, same rigor, own-site-only, null if not stated, asked two new
questions: does the church explicitly describe its space as a dedicated
building or as a shared/rented space (a school, a storefront, another
church's building), and what language(s) are services offered or
interpreted in. Coverage was far better than size: `meetingSpace` has a real
answer for **12 of 20** churches (6 confirmed shared/rented: Trinity Lake
Nona, East Coast Believers, Hope Presbyterian, Lake Nona Presbyterian PCA,
Adoration Church, Saint Frances Xavier Cabrini; 6 confirmed dedicated:
Spring of Life UMC, First UMC Orlando, All Saints Lutheran, Cathedral
Church of Saint Luke, Blessed Trinity Catholic, Faith Church Orlando).
`languageOptions` has a real answer for **10 of 20** churches, mostly
English plus Spanish, with Portuguese, ASL, and Arabic each showing up once.
Narcoossee Baptist Church's domain was unreachable in this environment
(network filtering blocked it on both passes); it needs a re-run from a
different network to get a real answer instead of `null`.

If Brian wants more size coverage in the future anyway, the remaining path is
off-site (calling churches, or reading
printed bulletins/annual reports that are not online at all), since the
online, own-site-only path has been run twice and is exhausted for this
batch.

**Candidate list change:** Journey of Life Lutheran Church (the original Lutheran
pick) no longer exists as an active congregation, its domain has expired and its
Facebook page confirms it is no longer an organized church. It was swapped for
**All Saints Lutheran Church (ELCA)**, a small Lutheran congregation in south
Orlando, verified active via its own site.

---

## Nona Church (Narcoossee Campus)
Nondenominational. Website: https://nonachurch.com/
- Locations / service times: https://nonachurch.com/locations
- Music style, dress norm, what to expect: https://nonachurch.com/im-new
- Kids ministry: https://nonachurch.com/get-connected/nonakids
- No stated attendance number or parking detail on the site, both null.

## Trinity Church of Lake Nona
Nondenominational (Reformed). Website: https://www.trinitylakenona.com/
- Service times, dress norm, kids ministry, parking, what to expect: https://www.trinitylakenona.com/faqs
- Music style: https://www.trinitylakenona.com/
- No stated attendance number, null.

## East Coast Believers Church (Lake Nona)
Nondenominational. Website: https://www.eastcoastbelievers.org/lake-nona
- All fields (address, service times, music, dress, kids, what to expect): https://www.eastcoastbelievers.org/lake-nona
- No parking note or attendance number on the site, both null.

## Azalea Park Church
Nondenominational. Website: https://azaleaparkchurch.org
- Address, service times, what to expect: https://azaleaparkchurch.org/about.html
- Site does not state music style, dress norm, size, kids ministry, or parking,
  all null. This is a small neighborhood church site with limited content.

## Narcoossee Baptist Church
Southern Baptist. Website: http://www.nbaptistchurch.org/
- Service times, what to expect: http://www.nbaptistchurch.org/worship.html
- Music style: http://www.nbaptistchurch.org/about.html
- Kids ministry: http://www.nbaptistchurch.org/ministries.html
- Site does not give a mailing address, dress norm, parking note, or attendance
  number, all null. Address recorded as null rather than guessed from map
  listings.

## South Orlando Baptist Church
Southern Baptist. Website: https://www.southorlandobaptist.org/
- Service times, music style, what to expect: https://www.southorlandobaptist.org/i-m-new
- Kids ministry: https://www.southorlandobaptist.org/children
- No dress norm, parking note, or attendance number stated, all null.

## First Baptist Church of Orlando
Southern Baptist. Website: https://www.firstorlando.com/
- Address, service times, music style, dress norm, parking, what to expect: https://www.firstorlando.com/locations/john-young/
- Kids ministry: https://www.firstorlando.com/kids/
- No attendance number stated on the campus page, null.

## Spring of Life United Methodist Church
United Methodist. Website: https://www.springchurch.org
- Address, service times, dress norm, kids ministry, parking, what to expect: https://www.springchurch.org/first-visit
- Site does not describe music style specifically, null. No attendance number, null.

## First United Methodist Church of Orlando
United Methodist. Website: https://firstchurchorlando.org
- Address, parking: https://firstchurchorlando.org/contact-us
- Service times, music style, what to expect: https://firstchurchorlando.org/services
- Kids ministry: https://firstchurchorlando.org/children
- No dress norm or attendance number stated, both null.

## Hope Presbyterian Church at Lake Nona
Presbyterian (PCUSA). Website: https://hopenona.com/
- Address, service times, music style, dress norm, kids ministry, what to expect: https://hopenona.com/directions-and-services
- No parking note or attendance number stated, both null.

## Lake Nona Presbyterian Church
Presbyterian (PCA). Website: https://www.lnpca.church/
- Address, service times, dress norm, what to expect: https://www.lnpca.church/i-am-new-here
- Site does not state music style, kids ministry, parking, or attendance number,
  all null. This is a likely-small congregation but the site never states a
  number, so sizeBand stays null rather than guessed.

## All Saints Lutheran Church
Lutheran (ELCA). Website: https://www.allsaintsorlando.org/
- Address: https://www.allsaintsorlando.org/contact-us
- Service times: https://www.allsaintsorlando.org/ (homepage lists 9:00 AM;
  note the visit/about pages list 9:30 AM instead, the site itself is
  inconsistent, flagged in whatToExpectNote)
- What to expect: https://www.allsaintsorlando.org/about
- Site does not state music style, dress norm, kids ministry, parking, or
  attendance number, all null.

## Cathedral Church of Saint Luke
Episcopal. Website: https://www.ccslorlando.org/
- Service times, music style, what to expect: https://www.ccslorlando.org/worship-times
- Kids ministry: https://www.ccslorlando.org/cathedral-kids
- Parking: https://www.ccslorlando.org/visit-us-1
- No dress norm or attendance number stated, both null.

## Adoration Church
Anglican (ACNA). Website: https://adorationchurchfl.com/
- Denomination confirmation: https://adorationchurchfl.com/beliefs
- Address, service times: https://adorationchurchfl.com/
- Kids ministry, what to expect: https://adorationchurchfl.com/adoration-kids
- No music style, dress norm, parking note, or attendance number stated, all
  null. Neighborhood corrected to Winter Park in churches.json to match the
  stated worship address, since the site's own copy elsewhere says "downtown
  Orlando" loosely but the actual meeting building is in Winter Park.

## Saint Frances Xavier Cabrini Catholic Church
Catholic. Website: https://stcabriniorlando.org/
- Address, service times: https://stcabriniorlando.org/mass-times/
- What to expect: https://stcabriniorlando.org/
- Site does not state music style, dress norm, kids ministry, parking, or
  attendance number, all null. Kids-during-Mass was deliberately left null
  rather than assumed "stay in Mass," the site does not say so explicitly.

## Blessed Trinity Catholic Church
Catholic. Website: https://btccorl.org/
- Address: https://btccorl.org/parish-office-and-directions
- Service times: https://btccorl.org/mass-times
- What to expect: https://btccorl.org/welcome
- No music style, dress norm, kids ministry, parking, or attendance number
  stated, all null. Site mentions "over 50 ministries and four Sunday Masses"
  but never gives a real attendance figure, so sizeBand stays null.

## St. George Antiochian Orthodox Church
Antiochian Orthodox. Website: https://www.stgeorgeorlando.org/home
- Service times, kids ministry: https://www.stgeorgeorlando.org/home
- Site has no dedicated visitor/what-to-expect page, no music style, dress
  norm, parking note, or attendance number, all null.

## Faith Church Orlando
Assemblies of God (Pentecostal). Website: https://faithchurchorlando.com/
- Address, service times, parking: https://faithchurchorlando.com/locations/curryford/
- Music style, dress norm, what to expect: https://faithchurchorlando.com/events/easter/
  (an Easter service page describing their normal weekly worship style and
  dress culture, not Easter-specific claims)
- Kids ministry: https://faithchurchorlando.com/kids/
- Size: https://faithchurchorlando.com/about/church/ states "By relocating to
  our Curry Ford property, we have been able to serve over 5,000 people as
  they pass through our doors each Sunday," recorded as sizeBand "Over a
  thousand on a Sunday." Found on the second, deeper research pass.

## Orlando Gospel Assembly
Assemblies of God (Pentecostal). Website: https://www.orlandogospelassembly.org/
- Address, service times: https://www.orlandogospelassembly.org/contact
- Site does not describe music style, dress norm, kids ministry, parking, or
  attendance number, all null. No dedicated visitor page found.

## Restoration Seventh-day Adventist Church
Seventh-day Adventist. Website: https://restorationfl.adventistchurch.org/
- Address, service times: https://restorationfl.adventistchurch.org/about-ii/
- What to expect: https://restorationfl.adventistchurch.org/
- No music style, dress norm, kids ministry, parking, or attendance number
  stated, all null. This church worships Saturday, not Sunday, recorded
  exactly as stated on the site.

## Greeters (data/greeters.json), added 2026-08-15

Unlike everything above, the greeters have NO sources because they are not
facts. Every greeter is a fictional demo persona invented for the challenge
build, two per church, and the app labels every card "Demo persona, not a
real member." No real person at any listed church has signed up for
anything. Each greeter's quote references only details that church publishes
on its own website (already sourced above), and every meeting spot is a
public location, most of them the church's own lobby, entrance, or guest
parking. If this ever goes live with real greeters, this section gets
replaced by a real vetting process through each church.
