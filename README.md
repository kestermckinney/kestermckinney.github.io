# kestermckinney.gitlab.io

Static GitLab Pages site for Paul McKinney and the featured projects:

- [ProjectNotes](https://gitlab.com/kestermckinney/ProjectNotes)
- [SqliteSyncPro](https://gitlab.com/kestermckinney/SqliteSyncPro)
- [SeeMyMac](https://gitlab.com/kestermckinney/SeeMyMac) (in development)
- [ScheduleIO](https://gitlab.com/kestermckinney/ScheduleIO)

## Structure

- `index.html` - personal and professional landing page
- `projects/seemymac.html` - SeeMyMac project page
- `projects/projectnotes.html` - ProjectNotes product page
- `projects/sqlitesyncpro.html` - SqliteSyncPro library page
- `images/scheduleio-logo.svg` - ScheduleIO project icon
- `images/scheduleio-avatar.png` - ScheduleIO GitLab project avatar
- `styles.css` - shared site styling
- `fonts/` - locally hosted Inter fonts and licenses
- `404.html` - fallback page

## Publishing

This site does not require Jekyll, npm, or Ruby. GitLab CI copies the static site into the `public` artifact and publishes it with GitLab Pages.

To publish on GitLab Pages:

1. Push this repository to the `main` branch of the `kestermckinney/kestermckinney.gitlab.io` GitLab project.
2. GitLab runs the `pages` job defined in `.gitlab-ci.yml`.
3. After the pipeline succeeds, the site is available at <https://kestermckinney.gitlab.io/>.

## Optional Next Steps

- Add a custom domain with a `CNAME` file if you want your own URL.
- Add an Open Graph social preview image for cleaner sharing.
- Extend the existing GitLab CI pipeline if you later want build steps or validation.
- Create a separate `kestermckinney` repository with a profile `README.md` if you also want a custom profile on `gitlab.com/kestermckinney`.
