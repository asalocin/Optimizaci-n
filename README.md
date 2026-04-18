# Apuntes de Inferencia Estadística — USACH 2026

Apuntes de la clase de Inferencia Estadística escritos en LaTeX, con un
workflow optimizado para **Visual Studio Code**.

---

## Estructura del repositorio

```
ApuntesInferencia/
├── main.tex                       ← documento raíz (compilar este archivo)
├── chapters/
│   ├── 01-introduccion.tex
│   ├── 02-estimacion-puntual.tex
│   ├── 03-intervalos-confianza.tex
│   └── 04-pruebas-hipotesis.tex
├── figuras/                       ← imágenes y gráficos (.pdf, .png, .jpg)
├── .vscode/
│   ├── settings.json              ← configuración de LaTeX Workshop
│   └── extensions.json            ← extensiones recomendadas
├── .github/
│   └── workflows/
│       └── compile-latex.yml      ← CI: compila el PDF en cada push
└── .gitignore                     ← ignora artefactos de compilación
```

---

## Configuración inicial (primera vez)

### 1 — Requisitos locales

| Herramienta | Instalación |
|---|---|
| [TeX Live](https://www.tug.org/texlive/) (Linux/macOS) o [MiKTeX](https://miktex.org/) (Windows) | Distribución LaTeX completa |
| [Visual Studio Code](https://code.visualstudio.com/) | Editor |
| Extensión **LaTeX Workshop** (`james-yu.latex-workshop`) | Compilación + preview integrado |

### 2 — Abrir el proyecto en VS Code

```bash
git clone https://github.com/asalocin/ApuntesInferencia.git
cd ApuntesInferencia
code .
```

VS Code sugerirá instalar las extensiones recomendadas (`.vscode/extensions.json`).
Acepta la instalación.

### 3 — Compilar

- **Automático**: al guardar cualquier archivo `.tex` se compila el documento.
- **Manual**: `Ctrl+Alt+B` (o `Cmd+Alt+B` en macOS).
- **Ver PDF**: `Ctrl+Alt+V` abre el visor integrado en un panel lateral.
- **SyncTeX** (ir del PDF al código fuente): `Ctrl+clic` en el PDF.

---

## Agregar una nueva sección/capítulo

1. Crea un archivo en `chapters/`, por ejemplo `chapters/05-regresion.tex`.
2. Agrega `\input{chapters/05-regresion}` en `main.tex` donde corresponda.
3. Guarda → LaTeX Workshop recompila automáticamente.

---

## CI/CD — Compilación automática en GitHub

El workflow `.github/workflows/compile-latex.yml` se ejecuta en cada `push`
que modifique archivos `.tex`:

- **Artefacto**: el PDF compilado queda disponible en la pestaña *Actions* →
  *Artifacts* durante 30 días.
- **Release**: cuando se hace push a `main`, el PDF se publica/actualiza
  automáticamente en *Releases* con el tag `pdf-latest`.

---

## Comandos LaTeX personalizados

Definidos en `main.tex`, disponibles en todos los capítulos:

| Comando | Significado |
|---|---|
| `\E` | Esperanza $\mathbb{E}$ |
| `\Var` | Varianza |
| `\Cov` | Covarianza |
| `\iid` | $\overset{\text{iid}}{\sim}$ |
| `\asim` | $\overset{a}{\sim}$ (asintóticamente) |
| `\plim` | $\xrightarrow{P}$ (convergencia en prob.) |
| `\dlim` | $\xrightarrow{d}$ (convergencia en dist.) |
| `\N` | Distribución Normal $\mathcal{N}$ |

### Entornos disponibles

```latex
\begin{defi}[Nombre]  ...  \end{defi}      % Definición
\begin{teo}[Nombre]   ...  \end{teo}       % Teorema
\begin{prop}          ...  \end{prop}      % Proposición
\begin{ejemplo}       ...  \end{ejemplo}   % Ejemplo
\begin{obs}           ...  \end{obs}       % Observación
\begin{resultado}     ...  \end{resultado} % Caja azul (resultado importante)
\begin{cuidado}       ...  \end{cuidado}   % Caja naranja (advertencia)
```

