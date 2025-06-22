# uniCenta oPOS 4.2 — Image-Size Fix  
**Full GPL-3 source · Patched installers for Windows & Linux**

---

## 🔍 What's the problem?

Editing a product in uniCenta oPOS 4.2 rewrites its image BLOB as **PNG** every time.  
After many edits the BLOB grows, slowing backups and any external sync (e.g. UniWebSales).

**Fix:** one-line change in `Utilities.writeImage()` — save as **JPG** instead of PNG.  

```java
ImageIO.write(img, "jpg", b);  // patch by Darío Carestia
```

Database size now remains stable.

---

## 📥 Downloads

Grab the assets in the latest release  
👉 <https://github.com/dariocarestia/unicenta-opos-imagefix/releases/latest>

| File                                    | Use case                               |
|-----------------------------------------|----------------------------------------|
| **unicentaopos-windows-installer.exe**  | Full Windows installer with the fix    |
| **unicentaopos4.2.jar**                 | Patched JAR — drop-in replacement      |

### Quick install (any platform)

1. Install stock uniCenta oPOS 4.2.  
2. Back-up the original `unicentaopos4.2.jar` in the program folder.  
3. Replace it with the patched JAR from the release.  
4. Start uniCenta — image sizes will no longer grow.

---

## 🛠 Source code & build

The complete GPL-3.0 source lives in **`/unicentaopos4.2-src`**.

```bash
cd unicentaopos4.2-src
ant clean dist        # builds dist/unicentaopos4.2.jar
```

Only one file is modified:

`unicentaopos4.2-src/src/com/openbravo/data/gui/Utilities.java`

---

## 📄 License

This fork remains under the GNU General Public License v3.0.  
Original project © uniCenta; patch © 2025 Darío Carestia.  
See COPYING for the full license text.


