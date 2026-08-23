# cs7150web

Source for <https://cs7150.baulab.info/> — Northeastern CS 7150, Deep Learning.

## Layout

Everything served by the website lives in `public/`, per the
[baulab.info website conventions](https://github.com/thebaulab/onramp/wiki/Websites-at-domain.baulab.info).

    public/index.html      redirect to the current semester
    public/.htaccess       force-download rules for documents
    public/2026-Fall/      current semester
    public/2025-Spring/    past semester
    public/2022-Fall       symlink -> /srv/baulab/www/files/cs7150/2022-Fall
    public/2023-Fall       symlink -> /srv/baulab/www/files/cs7150/2023-Fall

The 2022 and 2023 archives are about 11GB of lecture decks and datasets, far
too large for git, so they stay on the webserver disk under
`/srv/baulab/www/files/cs7150/` (also reachable at
<https://files.baulab.info/cs7150/>) and are linked in from `public/`.

## Deployment

A GitHub push webhook to `https://cs7150.baulab.info/push` makes the server
re-checkout this repo into `/srv/baulab/www/cs7150`. Apache serves
`/srv/baulab/www/cs7150/public`.

## Starting a new semester

1. `cp -r public/<last-semester> public/<new-semester>` and edit dates in `index.html`.
2. Point the redirect in `public/index.html` at the new directory.
3. Push.
