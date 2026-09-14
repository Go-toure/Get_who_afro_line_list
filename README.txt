AFRO Line List fetcher
=======================

Downloads the WHO AFRO polio line list (AllPolioviruses_20250106.xlsx)
from SharePoint and saves it as data/afro_line_list.xlsx.

Folder layout (keep these together -- copy the whole folder to move it
to another machine):

  fetch_afro_line_list.py     the script -- run this
  config/
    secrets.env.example       template -- copy to secrets.env and fill in
    secrets.env                (created automatically on first run)
  data/
    afro_line_list.xlsx       the downloaded file lands here
    backups/                   previous versions, timestamped

Setup (once per station):
  1. pip install requests
  2. python fetch_afro_line_list.py
     -> on the very first run, this creates config/secrets.env for you
        and stops with instructions.
  3. Open config/secrets.env and fill in:
       SHAREPOINT_TENANT_ID=...
       SHAREPOINT_CLIENT_ID=...
       SHAREPOINT_CLIENT_SECRET=...
     (Same three values already used by im_workflow / prepare_the_AFRO_
     SIA_Dashboard_input.py for this same SharePoint site -- copy them
     from wherever you already keep those, rather than requesting new
     ones.)
  4. Run it again: python fetch_afro_line_list.py

Every path the script uses is relative to its own folder, not to
whichever directory you happen to run it from -- so this whole folder
is portable: zip it, copy it, run it from any station once step 3 is
done there.

Useful options:
  python fetch_afro_line_list.py --output-name afro_line_list_2025.xlsx
  python fetch_afro_line_list.py --share-url "https://...a-different-file..."
  python fetch_afro_line_list.py --secrets-env "C:\path\to\other\secrets.env"
