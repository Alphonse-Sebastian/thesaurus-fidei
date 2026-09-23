# Thesaurus Fidei

*Treasury of the Faith.* A source-first Catholic study and reference platform,
covering the Church's treasury East and West.

The site brings the Catechism, the ecumenical councils, papal teaching and
Sacred Tradition into one ordered, searchable framework. It covers the Latin
Church and all twenty-three Eastern Catholic Churches with equal weight and
clear distinction. Commentary is there to orient and clarify. It does not
replace magisterial teaching, and every page points back to the primary text.

## Access

The site asks for an access phrase before it opens.

This is not a cosmetic check. The whole application, including the text of every
dossier, is encrypted with AES-256-GCM. The key is derived from the access
phrase with PBKDF2-SHA256 at 1,000,000 iterations. Only the salt, the
initialisation vector and the ciphertext are published. The phrase is not in
these files. Nothing readable appears until someone enters the correct phrase,
and a wrong phrase simply fails.

Keep the phrase safe. It is not stored here. If it is lost, this copy cannot be
opened and the site has to be built again from source.

### Limits

Encryption protects the contents from people who do not have the phrase. A
visitor, a search engine or anyone reading the page source sees only ciphertext.

It does not protect anything from a reader you give the phrase to. Once the page
opens, they have the text and can copy it. They can also pass the phrase on.
Treat it as a key to a room rather than a guarantee of secrecy.

The project source is not in this repository, on purpose. Publishing the source
next to the gate would put every dossier in plain text in a public repository,
which would defeat the point. The source is kept separately.

## Putting this online with GitHub Pages

The layout here is already correct. `index.html` is at the top level with
`assets/` next to it. Do not rename or move anything.

1. Sign in to GitHub and click **New** to create a repository.
2. Give it a name. Set it to **Public**. Tick **Add a README file**.
3. Click **Create repository**.
4. Click **Add file**, then **Upload files**.
5. Open this folder. Select everything inside it and drag it into the upload
   box. Wait for all of it to finish. The `assets/fonts` folder holds 37 files
   on its own, so this takes a moment.
6. Scroll down, type a short message such as `Initial upload`, and click
   **Commit changes**.
7. Go to **Settings**, then **Pages** in the left sidebar.
8. Under *Build and deployment*, set **Branch** to `main` and the folder to
   `/ (root)`. Click **Save**.
9. Wait about a minute and refresh. GitHub shows the live address at the top of
   that page.

A public repository is needed for GitHub Pages on a free account. That is fine
here, because everything published is encrypted.

### If something goes wrong

**Blank page or 404.** Check that `index.html` is at the top level of the
repository and not inside a subfolder. GitHub Pages serves the root of the
branch you picked.

**Page loads but looks unstyled.** The `assets` folder did not upload
completely. Check that `assets/styles.css` and the `assets/fonts` folder are
both there.

**Files seem to be missing.** Keep the `.nojekyll` file. Without it GitHub runs
Jekyll over the upload, which can skip files.

**Prompt appears but nothing happens on submit.** Check the address starts with
`https`. Browsers only provide the cryptography this uses on a secure
connection.

## Contents

```
index.html                     the site
assets/                        styles.css, emblem, 37 web fonts
Thesaurus-Fidei-offline.html   the whole site in one file
404.html                       fallback page
robots.txt                     keeps the site out of search results
.nojekyll                      required by GitHub Pages
```

The site is a single page application. It needs no server, no database and no
build step. Fonts, emblem and content are all included, so once it is open it
works without a connection.

`Thesaurus-Fidei-offline.html` is the same site in a single file, with the same
access phrase. Send that one to people. They open it, enter the phrase and read
it, with nothing to install.

## Rebuilding

Needs Node.js 22.13.0 or later, and the project source.

```bash
npm install
TF_SITE_PASSWORD='your access phrase' npm run build
```

On Windows PowerShell:

```powershell
$env:TF_SITE_PASSWORD = 'your access phrase'; npm run build
```

This writes two versions into `offline-dist/`:

- `Thesaurus_Fidei_Standalone.html`, the single file version
- `Thesaurus_Fidei_Website/`, an `index.html` with an `assets/` folder

To publish an update, copy what is inside `Thesaurus_Fidei_Website/` over the
`index.html` and `assets/` here.

Building without `TF_SITE_PASSWORD` produces an open site with no access phrase.
That is for checking your own work locally. Do not publish it.

`npm start` serves the built site on port 8080. `npm test` builds and checks the
output, including that a locked build contains no readable text.

## Reading the dossiers

Church profiles are built from compact modules grouped by study path. Each
module shows as a single line with its number, title, period and evidence label,
and opens where it sits. A map at the top of each profile lists every module and
jumps to it. Groups can be opened one at a time or all at once. Printing opens
everything automatically.

Claims carry a label: tradition, documented witness, secondary chronology,
reconstruction, dispute, official record, or editorial synthesis.

## Sources

The Syro-Malabar dossier draws on the Mar Ephrem Syriac-English Library
(Nasrani Media Learning), a shared research collection used with the permission
of its maintainers. Its 185 catalogued holdings are listed in the last section
of the dossier, each with its rights status. Works that are catalogued but were
not read are listed for further study only. They are not cited for any claim.

The theological modules rest on Archbishop Joseph Powathil, "Early Syriac
Theology: Some Basic Features", in Pauly Maniyattu (ed.), *East Syriac Theology:
An Introduction* (Satna: Ephrem's Publications, 2007), and on the Syro-Malabar
Eparchy of Great Britain, *Pastoral Plan 2022-2027: The Holy to the Holy Ones*.

## Editorial note

Reference edition. Profiles are developed from the project source library and
named ecclesial sources. Historical uncertainty, contested readings and
time-sensitive figures are labelled where they occur. Editorial commentary
supports study and orientation. It does not replace the teaching of the Church.
