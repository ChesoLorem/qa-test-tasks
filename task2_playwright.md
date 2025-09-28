# Задача 2: Playwright тест

## Условие
Написать тест, который открывает веб-страницу https://playwright.dev/ и проверяет, что заголовок страницы соответствует ожидаемому значению.  
Тест необходимо запустить минимум на 2 разных браузерах.

## Решение

```typescript
import { test, expect } from '@playwright/test';

test.describe('Проверка заголовка страницы playwright.dev', () => {
  test('Заголовок соответствует ожидаемому', async ({ page }) => {
    await page.goto('https://playwright.dev/');
    await expect(page).toHaveTitle('Fast and reliable end-to-end testing for modern web apps | Playwright');
  });
});
```

## Запуск на нескольких браузерах

В файле `playwright.config.ts` можно указать:

```typescript
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  projects: [
    {
      name: 'Chromium',
      use: { ...devices['Desktop Chrome'] },
    },
    {
      name: 'Firefox',
      use: { ...devices['Desktop Firefox'] },
    },
  ],
});
```

Запуск тестов:
```bash
npx playwright test
```
