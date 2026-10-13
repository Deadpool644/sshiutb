# sshiutb

TP **R202 : SSH --- TIPS & TRICKS** (clés, agent, bastion, tunnels, multiplexage).
Support de cours du module R202 / M2102, IUT Béziers.

Le document est un fichier LaTeX **autonome** : `ssh-indep.tex` contient son propre
préambule, il n'inclut aucun fichier externe et se compile n'importe où.

## Compilation

```bash
latexmk -pdf -shell-escape ssh-indep.tex
```

ou simplement :

```bash
make
```

Le `-shell-escape` est indispensable : le document utilise `minted` (coloration de code
via Pygments), qui appelle `pygmentize` depuis LaTeX.

Dépendances : TeXLive (classe `exam`, `minted2`, `babel` français, `hyperref`,
`microtype`, `xcolor`, `listings`, `enumitem`, `parskip`) et `pygments`.

`minted2.sty` (version Debian, licence LPPL) est **embarqué dans le dépôt** : il n'existe
que dans TeXLive Debian, pas dans TeXLive amont ni Ubuntu. LaTeX le trouve dans le
dossier courant, ce qui rend la compilation identique partout.

Sous Debian :

```bash
sudo apt install latexmk texlive-latex-base texlive-latex-recommended \
                 texlive-latex-extra texlive-fonts-recommended \
                 texlive-lang-french python3-pygments
```

## Contribuer

Le dépôt accepte les pull requests. Voir [CONTRIBUTING.md](CONTRIBUTING.md).

**Une PR ne peut être fusionnée que si la compilation LaTeX réussit** : le check
`compile` de la CI GitHub Actions est obligatoire sur la branche `main`. S'il est rouge
(erreur LaTeX, PDF absent ou vide, dépendance externe introduite), le bouton de merge
est bloqué.

## Contenu

| Fichier | Rôle |
|---|---|
| `ssh-indep.tex` | le TP, autonome (préambule inline) |
| `minted2.sty` | variante Debian de `minted`, embarquée (licence LPPL) |
| `LICENSE` | proposition de licence CC BY-SA 4.0 (en attente de décision) |
| `Makefile` | compilation locale |
| `.github/workflows/build.yml` | vérification de compilation sur chaque PR |

## Licence

**En attente de décision de l'auteur.** Une proposition CC BY-SA 4.0 est en cours
de discussion (voir la pull request « proposition de licence » et le fichier
`LICENSE`). Tant que cette proposition n'est pas fusionnée sur `main`, le dépôt
est **tous droits réservés**.

Si la proposition est acceptée, le support de cours (le `.tex` et le PDF) sera
libre de copie, d'adaptation et de rediffusion, à condition de citer l'auteur et
de diffuser les adaptations sous la même licence.

Le fichier `minted2.sty` n'est pas concerné : il garde sa propre licence LPPL
(Geoffrey M. Poore, Konrad Rudolph).
