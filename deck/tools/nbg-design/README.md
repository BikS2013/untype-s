# Vendored nbg-design scripts

A verbatim copy of the `scripts/` folder of the `nbg-design` Claude plugin (MIT, see `plugin.json` for the
version it was copied from). It exists so that `deck/build.sh` can run on GitHub Actions, where the plugin is
not installed: the deploy workflow sets `NBG_DESIGN_SKILL=deck/tools/nbg-design`.

Do not edit these files here. After updating the plugin locally, run `deck/tools/sync-nbg-design.sh` to refresh
this copy and commit the result; the next push then publishes the deck with the newer editing tools.
