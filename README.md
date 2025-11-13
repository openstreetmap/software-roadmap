# Core software roadmap

This is a proposed roadmap for OSM core software projects through 2026 and into 2027, based on conversations with a number of OSM community members. A lot is already going on day to day, but with the structure of a roadmap, prospective contributors and the broader community can have more clarity on priorities and expectations.

The roadmap is divided into four high-level themes. Under each theme are more specific focus areas, and under those are some representative examples of individual features we hope to land. Some items are well-defined and already discussed in the issue tracker, or even underway, while others will need refinement over time.

The roadmap focuses on what we can realistically accomplish if we can interest and/or pay people to work on these tasks. If an item is listed here, you can at least expect maintainers to take the matter seriously. On the other hand, this is not set in stone: if you know of something else we really should accomplish in this timeframe, please make a case for it so we can evaluate any tradeoffs. Question marks indicate features that need further discussion with stakeholders or that would be dependent on factors outside the scope of this project, but are still listed in order to give a full picture of the roadmapping discussions that have taken place.

## Community dynamics

The main website is essential to OSM. It mediates many interactions between community members and strongly influences overall community health. It focuses on basic functionality, leaving more advanced derivative tools to the broader ecosystem.

Unfortunately, perceived shortcomings in functionality or user experience have led the community to rely too heavily on third-party platforms for communication and coordination. Second-party tools now work around some missing features, but these tools aren’t discoverable enough for the vast majority of users.

With the recent launch of vector tiles, we’re giving users another reason to give the main site another look. Let’s bring the center of attention back here and help mappers contribute more productively.

* Integrate vector tiles into the website beyond the [initial Leaflet-based launch](https://github.com/openstreetmap/openstreetmap-website/pull/6137)
    * [Migrate](https://github.com/gravitystorm/openstreetmap-website/issues/289) from Leaflet to MapLibre
    * Take advantage of vector capabilities (e.g., togglable layers, live data inspector, [globe view](https://community.openstreetmap.org/t/everything-is-relative-equal-earth-projection-vs-mercator/134608/3), translations, larger text for accessibility, dark mode)
* Facilitate communication among users
    * [Notifications](https://github.com/openstreetmap/openstreetmap-website/issues/1387) about [changeset](https://github.com/openstreetmap/openstreetmap-website/issues/3182), diary comments ([thanks?](https://github.com/openstreetmap/openstreetmap-website/issues/875))
    * Further [community index](https://github.com/openstreetmap/openstreetmap-website/issues/2795) integration (chip away at Microcosms concept)
    * Integrate diaries and the forum?
* Antispam/moderation tools to reduce operations team workload
    * Review and revise spam score metrics
    * Make user list accessible beyond admins?
    * [Activity logs](https://github.com/openstreetmap/openstreetmap-website/issues/5298)
* More robust history view
    * Filtering history by more criteria
    * Augmented diff generation that doesn’t depend on external DB mirror
    * Visualize tag and geometry changes
* Note management
    * [Metadata on notes](https://github.com/openstreetmap/openstreetmap-website/pull/5904)
    * [Filtering notes](https://github.com/openstreetmap/openstreetmap-website/issues/486) by more than geography (age/date, tags, search terms?)
    * Notes near home
* Integrate third-party tools
    * Expose more search, routing, querying capabilities
    * Overlays from QA tools
    * Link out to more advanced third-party tools for [history](https://github.com/openstreetmap/openstreetmap-website/issues/2629), extracts, raw tag editing, etc.
    * Link to applications on mobile platforms
* Engaging user content
    * CTAs to contribute when logged out (on element detail pages, notes, etc.), possibly informed by Piwik stats
    * User profile widgets
    * Markdown in more places
* Avoid duplicate uploads

## Operational sustainability

This is a mix of development and operations work. There are several areas that could become urgent and costly for the operations team if we don’t pay down technical debt.

* Speed up planet dumps
    * Change compression setting during database backup (expected halving of processing time; requires Postgres upgrade)
* Improve resilience of diff generation
    * Synchronize timestamp across machines (possibly in the cloud)
    * Automate failover including edge cases
    * [Replace osm-logical with something more mainstream](https://github.com/openstreetmap/osmdbt/issues/38)
* Improve large relation performance on Rails
* More efficient API queries for GPX traces (potential breaking change)
* Allow cleanup of GPX traces to reclaim storage space (requires outside help)
    * Reconstitute source ZIP files
* Modernize website architecture
    * Migrate frontend to turbo, webpack
    * Pull in iD and other dependencies via NPM
    * Migrate authentication to third-party library (e.g., devise)
* Streamline contributor setup

## Developer experience

This theme is purposely light on actual technical changes. There is a consensus that the longstanding dream of [data model evolution](https://github.com/osmlab/osm-data-model/) and [API v0.7](https://wiki.openstreetmap.org/wiki/API_v0.7) is still out of reach given current funding levels and timeframe. The biggest impact we can have is to explain the project to developers on our terms instead of allowing competing platforms to define us.

* Communicate with developers running instances, forks, data consumers
    * Identify stakeholders for any future breaking API change
    * [Convenient tracking](https://github.com/openstreetmap/owg-website/issues/90) of security incidents and other reports
* Improve documentation
    * Modernize and translate switch2osm and welcome mat
    * Machine readable API and documentation, self-documenting API code ([Swagger](https://github.com/openstreetmap/openstreetmap-website/issues/3107) etc.)
    * Recipes for orchestrating low-level tools
    * Guides for developers coming from traditional GIS, proprietary map platforms, Overture (understanding data model, how we think about persistent identifiers, etc.)
* More output formats, extracts?

## Legal compliance

The legal landscape for open data projects has gotten more complex in recent years. Changes in this area have real tradeoffs and will not be popular with parts of the community. Nevertheless, as OSM grows in popularity and influence, we need to manage our legal risk. Any move of the OSMF to a different country may significantly affect the requirements in this space.

* Terms of service acceptance
* [Options](https://github.com/openstreetmap/openstreetmap-website/issues/5804) for showing aggregated content on user profiles
* Filter PII out of certain API calls, planet dumps for GDPR compliance
* Any other items needed for OSA and DSA compliance as they come up
