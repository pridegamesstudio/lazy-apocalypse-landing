### Настройка окружения:
> Нужна NodeJS 20. Можно поставить через nvm https://github.com/nvm-sh/nvm
```sh
nvm use 20
```

### Сборка:
```sh
npm install
```

```sh
npm run build
```

```sh
npm run generate
```

### Запуск сборки локально:
```sh
npx serve .output/public
```

### Деплой (статика):
Из папки `.output/public` загрузить файлы на html хостинг.

### Разработка
```sh
npm run dev
```
