# Claude Toolkit — Backup de Skills

Backup privado de las skills instaladas en Claude Code (`~/.agents/skills/`).

## Agregar skill nueva al backup

Después de instalar una skill nueva con `npx skills add`:

```bash
cd ~/.agents/skills && git add . && git commit -m "Add [nombre-skill]" && git push
```

## Recuperar todo en un PC nuevo

```bash
git clone https://github.com/nelsonur17-alt/claude-toolkit.git ~/.agents/skills
```
