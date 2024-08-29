# E2E Testy

## Druhy testů

- Manual
- E2E (UI)
- API (Contract)
- Component (Integration)
- Unit

## Porovnání E2E knihoven

- Selenium (2004)
  - Nejstarší 🦖
  - Hlavně Java
  - Nejhorší DX

- WebdriverIO (2006)
  - Selenium 2.0
  - Mobile

- Puppeteer (2017)
  - Google
  - Jenom Chrome (Firefox od 23.0.0 (2024-08-07), Safari ne)
  - Primárně na automatizaci prohlížeče (web scraping, screenshoty, PDF)

- Cypress (2018)
  - Chrome a Firefox (Safari experimental přes Playwright)
  - Jednoduchý setup
  - Testy běží přímo v prohlížeči - nejsou potřeba binaries
  - pseudo promise chaining - `.then` - [callback hell](https://mtlynch.io/notes/cypress-vs-playwright/#playwright-requires-less-domain-specific-knowledge)
  - Pomalejší
  - Primárně na lokální testování
  - Paralelizované testy jenom za $$$ (nebo 3rd party)
  - [Dashboard](https://docs.cypress.io/guides/cloud/introduction)
  - Neumí hover, file upload, iframe, taby
  - [Shadow DOM je pain](https://mtlynch.io/notes/cypress-vs-playwright/#playwright-makes-it-easier-to-navigate-the-shadow-dom)

- Playwright (2020)
  - Microsoft (team co dělal Puppeteer)
  - Všechny prohlížeče
  - Více tabů najednou
  - Defaultně je vše paralelní
  - Nejlepší DX
  - VSCode a Jetbrains integrace
  - Normální JS async/await (žádná divná Cypress event loop)
  - [Konzistentní API](https://mtlynch.io/notes/cypress-vs-playwright/#playwright-exposes-a-consistent-set-of-assertions)
  - JS, TS, Python, Java, C#
  - Složitější setup
  - `@playwright/test` x `playwright` - jako Puppeteer


- [NPM stažení](https://npmtrends.com/-vs-Puppeteer-vs-cypress-vs-playwright-vs-puppeteer-vs-selenium-webdriver-vs-webdriverio) (All time)


- https://github.com/microsoft/playwright/issues
- https://github.com/cypress-io/cypress/issues
- https://ossinsight.io/analyze/microsoft/playwright?vs=cypress-io%2Fcypress
- Celkový počet issues vs počet otevřených


- Benchmarky (single thread)
[1](https://www.checklyhq.com/blog/cypress-vs-selenium-vs-playwright-vs-puppeteer-speed-comparison/#conclusion)
[2](https://ray.run/blog/comparing-automated-testing-tools-cypress-selenium-playwright-and-puppeteer#benchmarks)

## Ukázka

- Movues
  - UI mode
    - `playwright test --ui`
    - Open in vscode
    - Watch mode
    - taby `console`, `network`, `source`
    - Errory - `tmdbDetails` L125
    - `playwright codegen` - vyplnění tokenu, save, refresh, assert
    - `npx playwright test --debug`
  - CLI mode
    - `playwright test`
    - Debugging - webstorm integrace, vscode extension
    - CI - workflows, docker
    - Trace + html report

- Delta maska

## Závěr

- Intuitivní API a dokumentace
- Hledání problémů
  - Github issues
  - SO (2020 - výhoda i nevýhoda)
  - ChatGPT
- Kdy spouštět testy?
  - Ideálně watch mode
  - E2E jsou pomalé, flaky
  - V CI ne vždy realistické
  - Na nečem co je "deployable" (https://login.cesys.eu/)

## Další odkazy
- [On Migrating from Cypress to Playwright](https://mtlynch.io/notes/cypress-vs-playwright)
- [Porovnání knihoven a kódu](https://ray.run/blog/comparing-automated-testing-tools-cypress-selenium-playwright-and-puppeteer)
- https://old.reddit.com/r/QualityAssurance/comments/srhafv/cypress_vs_playwright/hwsa7pu/
- https://ray.run/blog/the-rapid-adoption-of-playwright-test-in-software-qa
- https://ossinsight.io/collections/testing-tools/trends/
- Dokumentace

## Názvosloví
- Flake, Flaky test - testy, které někdy projdou a někdy ne, bez změny kódu, nepředvídatelné, nespolehlivé (cypress x playwright)
- Regrese - bug, který byl už jednou opraven se znovu objevil
- Regression testing - testy, že se nerozbilo to co už jednou fungovalo
- Story - popis jak má část softwaru fungovat ("As a customer, I want to be able to reset my password so that I can regain access to my account if I forget it.")
- Sanity / smoke / confidence / acceptance testy
  - (předtest)
  - Základní věci jako že se načte stránka, funguje login
  - Když projde, tak se mohou spustit další testy
