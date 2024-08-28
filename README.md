# E2E Testy

## Druhy testů

- unit
- integration
- **E2E**
- smoke


## Porovnání E2E knihoven

[NPM stažení](https://npmtrends.com/-vs-Puppeteer-vs-cypress-vs-playwright-vs-puppeteer-vs-selenium-webdriver-vs-webdriverio) (All time)

- Playwright (2020)
  - Microsoft
  - Všechny prohlížeče
  - Více tabů najednou
  - Defaultně je vše paralelní
  - Nejlepší DX
  - VSCode a Jetbrains integrace
  - Normální JS async/await (žádná divná Cypress event loop)
  - JS, TS, Python, Java, C#
  - Složitější setup
- Cypress (2018)
  - Chrome a Firefox (Safari experimental přes Playwright)
  - Jednoduchý setup
  - pseudo promise chaining - `.then` - callback hell
  - Pomalejší
  - Primárně na lokální testování
  - Paralelizované testy jenom za $$$ (nebo 3rd party)
  - [Dashboard](https://docs.cypress.io/guides/cloud/introduction)
- Puppeteer (2017)
  - Google
  - Jenom Chrome (Firefox od 23.0.0 (2024-08-07), Safari ne)
- Selenium (2004)
  - Nejstarší 🦖
  - Hlavně Java
  - Nejhorší DX
- WebdriverIO (2006)
  - Selenium 2.0
  - Mobile


- https://github.com/microsoft/playwright/issues
- https://github.com/cypress-io/cypress/issues

[Benchmark](https://www.checklyhq.com/blog/cypress-vs-selenium-vs-playwright-vs-puppeteer-speed-comparison/#conclusion)

## Ukázka

- Movues
  - UI mode
    - Open in vscode
    - Watch mode
    - console, network, source
    - Errory - `tmdbDetails` L125
    - `codegen` - vyplnění tokenu, save, refresh, assert
  - CLI mode
    - Debugging - webstorm, vscode ještě lepší
    - CI - workflows, docker
    - Trace + html report

- Delta maska

## Závěr

- Intuitivní API
- Super dokumentace
- Hledání problémů
  - Github issues
  - SO (2020 - výhoda i nevýhoda)
  - ChatGPT


## Názvosloví
- Flake, Flaky test - testy, které někdy projdou a někdy ne, bez změny kódu, nepředvídatelné, nespolehlivé (cypress x playwright)
- Regrese - bug, který byl už jednou opraven se znovu objevil
