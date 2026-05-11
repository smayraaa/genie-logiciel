# bloom · Cycle & Mood — JavaFX

Application de suivi de cycle menstruel convertie de HTML/CSS vers JavaFX (fichier unique).

## Structure

```
BloomCycleMood.java   ← source complète (1 seul fichier)
run_bloom.sh          ← script de lancement (Linux/macOS)
```

## Prérequis

- **Java 11+** (OpenJDK recommandé)
- **JavaFX 11+**

### Installation rapide (Ubuntu / Debian)

```bash
sudo apt install openjdk-21-jdk openjfx
```

### Windows / macOS

1. Télécharger JavaFX SDK depuis https://gluonhq.com/products/javafx/
2. Décompresser en `javafx-sdk/` à côté du fichier source
3. Compiler et lancer :

```bash
# Compiler
javac -cp "javafx-sdk/lib/*" BloomCycleMood.java

# Lancer
java -cp ".:javafx-sdk/lib/*" BloomCycleMood
```

## Lancement rapide (Linux)

```bash
bash run_bloom.sh
```

## Fonctionnalités implémentées

| Section | Statut |
|---|---|
| Topbar (marque, date, phase, bouton Mon cycle) | ✅ |
| Bannière période active (avec barre de progression) | ✅ |
| Sidebar — anneau de cycle SVG-like (Canvas) | ✅ |
| Sidebar — navigation entre phases | ✅ |
| Sidebar — checklist quotidienne (toggle) | ✅ |
| Hero banner avec anneau + infos phase | ✅ |
| Statistiques (3 cards) | ✅ |
| Fenêtre sensible + sélection d'humeur | ✅ |
| Recommandations (grille 2×2) | ✅ |
| Intensité des symptômes (progress bars animées) | ✅ |
| Actions rapides (Save + AI Report) | ✅ |
| Modal d'onboarding 3 étapes | ✅ |
| Toast notifications | ✅ |

## Notes d'architecture

- **Fichier unique** : toute l'UI, la logique et les données sont dans `BloomCycleMood.java`
- Les anneaux de cycle sont dessinés via `Canvas` + `GraphicsContext` (équivalent SVG)
- L'onboarding s'ouvre via une `Stage` modale (`Modality.WINDOW_MODAL`)
- Les barres de symptômes s'animent au chargement via `Timeline`
- Compatible Java 11 (pas de switch expressions ni de pattern matching)
