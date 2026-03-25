# APK-Hosting via GitHub Releases (kostenlos, bis zu 2 GB pro Datei)
# ===================================================================
#
# ANLEITUNG:
#
# 1. Gehe zu:
#    https://github.com/jakobneukirchner/k12apps-updatechecker/releases/new
#
# 2. Erstelle einen neuen Tag:  Hashi-v1.0.0
#    Titel:                     Hashi v1.0.0
#
# 3. Lade die release.apk als Anhang hoch ("Attach binaries to this release")
#
# 4. Klicke auf "Publish release"
#
# 5. Der Download-Link lautet dann:
#    https://github.com/jakobneukirchner/k12apps-updatechecker/releases/download/Hashi-v1.0.0/release.apk
#
# 6. Trage diesen Link in apps/Hashi/versions.json ein:
#
#    {
#      "latest": "1.0.0",
#      "versions": [
#        {
#          "version": "1.0.0",
#          "apk": "https://github.com/jakobneukirchner/k12apps-updatechecker/releases/download/Hashi-v1.0.0/release.apk",
#          "changelog": "Erste Veroeffentlichung"
#        }
#      ]
#    }
#
# NEUE VERSION veroeffentlichen:
#  - Neuen Release mit Tag z.B. "Hashi-v1.1.0" erstellen
#  - Neue APK hochladen
#  - In versions.json "latest" auf "1.1.0" setzen + neuen Eintrag ergaenzen
#  - Commit pushen -> Netlify deployed automatisch
#
# VERSIONSVERGLEICH:
#  Der Updater vergleicht semantisch korrekt:
#  1.0.0 < 1.0.1 < 1.1.0 < 2.0.0
#  Jede Stelle wird als Zahl verglichen, nicht als String.
