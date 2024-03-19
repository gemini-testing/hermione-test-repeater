# hermione-test-repeater

## Обзор

Используйте плагин [hermione-test-repeater][hermione-test-repeater], чтобы запустить один и тот же тест (или группу тестов) требуемое количество раз.

Данный плагин может пригодиться в тех случаях, когда нужно убедиться в стабильности написанных тестов. Плагин гарантирует, что тесты будут запущены столько раз, сколько вы задали, независимо от результатов их прогона в каждой попытке. Кроме того, плагин позволяет запускать тесты каждый раз в новой сессии браузера. Это исключает влияние деградации браузера или еще какие-либо побочные эффекты, которые могли бы возникнуть при повторных прогонах в одной и той же сессии браузера.

## Установка

```bash
npm install -D hermione-test-repeater
```

## Настройка

Необходимо подключить плагин в разделе `plugins` конфига `hermione`:

```javascript
module.exports = {
    plugins: {
        'hermione-test-repeater': {
            enabled: true,
            repeat: 50,
            minRepeat: 10,
            maxRepeat: 100,
            uniqSession: true
        },

        // другие плагины гермионы...
    },

    // другие настройки гермионы...
}
```

### Расшифровка параметров конфигурации

| **Параметр** | **Тип** | **По&nbsp;умолчанию** | **Описание** |
| :--- | :---: | :---: | :--- |
| enabled | Boolean | true | Включить / отключить плагин. |
| repeat | Number | 0 | Сколько раз нужно запустить тест, независимо от результата от его прогона. |
| minRepeat | Number | 0 | Минимальное количество раз, которые можно запустить тест. |
| maxRepeat | Number | Infinity | Максимальное количество раз, которые можно запустить тест. |
| uniqSession | Boolean | true | Запускать каждый тест в уникальной сессии браузера. |

### Передача параметров через CLI

Все параметры плагина, которые можно определить в конфиге, можно также передать в виде опций командной строки или через переменные окружения во время запуска гермионы. Используйте префикс `--test-repeater-` для опций командной строки и `hermione_test_repeater_` &mdash; для переменных окружения. Например:

```bash
npx hermione --test-repeater-repeat 5
```

```bash
hermione_test_repeater_repeat=5 npx hermione
```

## Использование

### Опция --repeat

Также плагин добавляет к [CLI][cli] гермионы специальную опцию `--repeat`, с помощью которой можно запустить тест нужное количество раз более удобным образом. Например:

```bash
npx hermione --repeat 5
```

[cli]: https://ru.wikipedia.org/wiki/Интерфейс_командной_строки

## Полезные ссылки

* [Исходники плагина hermione-test-repeater][hermione-test-repeater]

[hermione-test-repeater]: https://github.com/gemini-testing/hermione-test-repeater
[cli]: https://ru.wikipedia.org/wiki/Интерфейс_командной_строки