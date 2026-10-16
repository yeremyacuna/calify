# Publish Approved Option 01 Branding

**Release status:** Original binaries not yet committed. This guide exists to finish the publication with no image substitutions or broken README links.

## Required assets

Six image/PDF assets are maintained in the prepared `Calify_Branding_Release_Ready.zip`, under `assets/branding/official/` and `assets/branding/reference/`. Their complete source hashes are in [Original Asset Manifest](../../assets/branding/ORIGINAL_ASSET_MANIFEST.json).

The current GitHub connector supports text/Git objects but does not directly transfer local binary files into a Git blob. The package therefore includes an independently smoke-tested Python release script that performs the binary copy inside the authorized user's local Git checkout.

## Publish on Windows

1. Download and extract `Calify_Branding_Release_Ready.zip` from the Calify project conversation.
2. Make sure Git and Python 3 are installed and GitHub authentication is set up.
3. In a **clean** local clone of `yeremyacuna/calify`, run:

```powershell
git checkout main
git pull --ff-only origin main
python "C:\Users\YOUR_USER\Downloads\Calify_Branding_Release_Ready\scripts\publish_official_branding.py" "C:\Users\YOUR_USER\Downloads\Calify_Branding_Release_Ready.zip" --commit --push
```

The publisher refuses a dirty checkout, unexpected remote or branch, missing source, or checksum mismatch. It copies the verified originals, adds a binary `.gitattributes`, versions its own source, and updates the GitHub README **in the same commit** as the images. Without `--commit --push`, it stages files for manual review.

4. Open GitHub and verify that the approved logo, banner and design-gallery images render correctly. Update `v2` through the documented branching workflow after approval.

**Never** upload the personal iOS Shortcut, live API tokens or private academic trackers as part of this branding release.
