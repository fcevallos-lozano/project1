# IHP SG13G2 — Where to Find What

Quick reference for which files/folders you need for each design flow, and how to
push your own work to your own GitHub repo. All paths below are relative to this
folder (`GITHUB_PDK_TOOLS/`).

---

## 1. Schematic capture (xschem)

| What | Where |
|---|---|
| Primitive device symbols (transistors, caps, res, diodes, bjt...) | `ihp-sg13g2/libs.tech/xschem/sg13g2_pr/*.sym` |
| Standard cell symbols/schematics | `ihp-sg13g2/libs.ref/sg13g2_stdcell/sch/`, `.../sym/` |
| Example testbenches | `ihp-sg13g2/libs.tech/xschem/sg13g2_tests/` (ngspice) and `sg13g2_tests_xyce/` (Xyce) |
| xschem simulation setup files | `ihp-sg13g2/libs.tech/xschem/simulations/` |

Start a new schematic in xschem, then add primitive devices from `sg13g2_pr` — xschem
needs its library path pointed at that folder (usually done in your `xschemrc`).

## 2. SPICE / circuit simulation (ngspice, Xyce, Qucs-S)

| What | Where |
|---|---|
| ngspice device models | `ihp-sg13g2/libs.tech/ngspice/models/` |
| Xyce device models | `ihp-sg13g2/libs.tech/xyce/models/` |
| Verilog-A compact models (PSP103, MOSVAR, r3_cmc, etc.) | `ihp-sg13g2/libs.tech/verilog-a/` |
| Qucs-S symbols/examples | `ihp-sg13g2/libs.tech/qucs-s/` |
| Cell-level SPICE/CDL netlists (for LVS reference) | `ihp-sg13g2/libs.ref/<cellset>/spice/` and `.../cdl/` |
| Measured device data (MDM format) | `ihp-sg13g2/libs.doc/meas/` (HBT, MOS, pnpMPA) |

## 3. Layout

| What | Where |
|---|---|
| KLayout tech file (layers, DRC/LVS menu hookup) | `ihp-sg13g2/libs.tech/klayout/tech/sg13g2.lyt`, `.lyp` |
| KLayout PyCells (parametric devices) | `ihp-sg13g2/libs.tech/klayout/python/` |
| Magic tech + device generator scripts | `ihp-sg13g2/libs.tech/magic/ihp-sg13g2.tech`, `*.tcl` |
| Magic startup rc file (load this to launch with the PDK) | `ihp-sg13g2/libs.tech/magic/ihp-sg13g2.magicrc` |
| Reference GDS for primitives | `ihp-sg13g2/libs.ref/sg13g2_pr/gds/sg13g2_pr.gds` |
| Reference GDS for stdcells / IO / SRAM | `ihp-sg13g2/libs.ref/sg13g2_stdcell/gds/`, `sg13g2_io/gds/`, `sg13g2_sram/gds/` |
| LEF (for P&R / floorplanning) | `ihp-sg13g2/libs.ref/<cellset>/lef/` |

## 4. DRC (Design Rule Check)

| What | Where |
|---|---|
| KLayout DRC main script | `ihp-sg13g2/libs.tech/klayout/tech/drc/ihp-sg13g2.drc` |
| KLayout DRC rule decks (per-check breakdown) | `ihp-sg13g2/libs.tech/klayout/tech/drc/rule_decks/` |
| DRC rule docs (human-readable) | `ihp-sg13g2/libs.tech/klayout/tech/drc/docs/main_rules.md`, `extra_rules.md`, `precheck_rules.md` |
| Run DRC from command line | `ihp-sg13g2/libs.tech/klayout/tech/drc/run_drc.py` |
| Magic DRC tech rules | `ihp-sg13g2/libs.tech/magic/ihp-sg13g2-drc.tech` |
| Official layout rules PDF | `ihp-sg13g2/libs.doc/doc/SG13G2_os_layout_rules.pdf` |

## 5. LVS (Layout vs. Schematic)

| What | Where |
|---|---|
| KLayout LVS main script | `ihp-sg13g2/libs.tech/klayout/tech/lvs/sg13g2.lvs` |
| KLayout LVS rule decks (per-device extraction/connections) | `ihp-sg13g2/libs.tech/klayout/tech/lvs/rule_decks/` |
| Run LVS from command line | `ihp-sg13g2/libs.tech/klayout/tech/lvs/run_lvs.py` |
| netgen setup (alternative LVS engine, pairs with Magic) | `ihp-sg13g2/libs.tech/netgen/ihp-sg13g2_setup.tcl` |
| Reference CDL netlists to compare layout against | `ihp-sg13g2/libs.ref/<cellset>/cdl/` |

## 6. Parasitic extraction

| What | Where |
|---|---|
| Interconnect tech file (RC coefficients) for extraction tools | `ihp-sg13g2/libs.tech/parasitics/itf/` |
| Magic extract rules | `ihp-sg13g2/libs.tech/magic/ihp-sg13g2-extract.tech` |
| OpenROAD's RCX (part of the librelane digital flow) | `ihp-sg13g2/libs.tech/librelane/openrcx/` |

## 7. Digital flow (synthesis / place & route)

| What | Where |
|---|---|
| Liberty timing (.lib) | `ihp-sg13g2/libs.ref/sg13g2_stdcell/lib/`, `sg13g2_io/lib/`, `sg13g2_sram/lib/` |
| LEF (abstract layout for P&R) | same cellsets, `lef/` subfolder |
| Verilog behavioral models | same cellsets, `verilog/` subfolder |
| OpenROAD config | `ihp-sg13g2/libs.tech/openroad/` |
| LibreLane config (stdcell + IO) | `ihp-sg13g2/libs.tech/librelane/sg13g2_stdcell/`, `sg13g2_io/` |
| Alternate digital stdcell set (submodule) | `ihp-sg13g2/libs.tech/digital/` |

## 8. EM simulation (RF/passives)

| What | Where |
|---|---|
| OpenEMS scripts/tutorials (submodule) | `ihp-sg13g2/libs.tech/openems/openems_ihp_sg13g2/` |
| Palace (FEM solver) scripts (submodule) | `ihp-sg13g2/libs.tech/palace/` |

## 9. Process documentation

| What | Where |
|---|---|
| Process specification PDF | `ihp-sg13g2/libs.doc/doc/SG13G2_os_process_spec.pdf` |
| Layout rules PDF | `ihp-sg13g2/libs.doc/doc/SG13G2_os_layout_rules.pdf` |
| EM simulation overview PDF | `ihp-sg13g2/libs.doc/doc/EM_Simulation_Overview.pdf` |
| Tested tool versions | `versions.txt` (repo root) |

---

## 10. Pushing your own work to your own GitHub repo

This clone's `origin` currently points at IHP's official upstream repo
(`https://github.com/IHP-GmbH/IHP-Open-PDK.git`), which you don't have push
access to. To save your own changes (new cells, notes, test setups) to a repo
you control, do this **one-time setup**, then a regular save routine.

### One-time setup

1. **Set your git identity** (required before any commit — not yet configured
   on this machine):
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-github-email@example.com"
   ```

2. **Create your own GitHub repo.** Either:
   - Fork `IHP-GmbH/IHP-Open-PDK` on github.com (keeps upstream history, makes
     it easy to pull in IHP's future updates), or
   - Create a brand-new empty repo (e.g. `my-ihp-sg13g2-work`) if you don't
     need upstream history.

3. **Re-point your remotes** so `origin` is *your* repo and `upstream` is
   IHP's:
   ```bash
   git remote rename origin upstream
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

### Every time you want to save/upload changes

```bash
git status                      # see what changed
git add <files-you-changed>     # stage specific files (avoid `git add -A` blindly)
git commit -m "short description of what changed"
git push                        # sends it to your GitHub repo
```

### Pulling in IHP's future updates (optional, only if you forked)

```bash
git fetch upstream
git merge upstream/main         # or upstream/dev, depending on which branch you track
```

### Notes

- GDS files are binary and can be large — git will still version them fine,
  just don't expect readable diffs.
- If GitHub ever asks for a password over HTTPS, it wants a
  [personal access token](https://github.com/settings/tokens), not your
  account password — or set up SSH keys instead and use an `git@github.com:...`
  remote URL.
- Never commit API keys or credentials into this repo, even in a `.env` or
  scratch file — GitHub history is effectively permanent once pushed.
