---
dusk: v1alpha1
namespace: stout
kind: repository
name: stout.dog
title: My Doggos
attributes:
  language: jekyll
  visibility: public
  deploys_to: cloudflare-workers
  url: https://www.stout.dog
---

A small Jekyll site documenting the three family dogs.
It exists for one situation: their collar tags link here, so whoever finds a lost dog lands on that dog's page with its photos, its microchip registry and number, and both owners' phone numbers already on screen.

A dog is one file in the `_doggos/` collection, its front matter carrying breed, weight, birthday, microchip details, an ordered image list for the slideshow, vaccines with expiry dates, and links to scanned vet records.
Images and PDFs go under `assets/records/<name>/`, matching the `assets` key in that dog's front matter.
Owner names, phone numbers and the home town live in `_config.yml` rather than in any page, so a change to contact details is one edit.

Deployment is `jekyll build` into `_site/`, served as Cloudflare Workers static assets per `wrangler.jsonc`.
It was on GitHub Pages first; the `CNAME` has been removed and the custom domain is a Workers route now.

## Gotchas

**Everything here is public on purpose, vet PDFs and phone numbers included**, because a stranger holding the dog has to be able to read it without an account. Treat anything added to this repository as world-readable, and do not put a record here that you would not hand to whoever picks the dog up.

**Nothing checks the vaccine `expiration` dates.** The layout prints them verbatim, so a lapsed rabies date reads exactly like a current one. Keeping them true is a manual job.
