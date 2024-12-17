# Коллекция архивов сайтов (культурная жизнь города Усть-Илимска)

Данный репозиторий представляет собой тематическую коллекцию архивов вебсайтов. Коллекция создана с помощью unix-утилиты [`wget`](https://ru.wikipedia.org/wiki/Wget), описание метаданных получено с помощью пакета [`metawarc`](https://github.com/datacoon/metawarc). Также коллекция содержит краткое описание результатов анализа сайтов с точки зрения архивопригодности; анализ проведён с помощью ресурса [ArchiveReady](https://archiveready.com/) по метрикам [`CLEAR`](http://purl.pt/24107/1/iPres2013_PDF/CLEAR%20a%20credible%20method%20to%20evaluate%20website%20archivability.pdf).


## Краткое описание

Данная архивная коллекция представляет собой собрание сайтов, посвящённых культурной жизни города Усть-Илимска Иркутской области. В коллекцию вошли ресурсы музеев, дворцов культуры и других культурных учреждений города.

Усть-Илимск – небольшой (менее 80 тысяч жителей) город на севере Иркутской области, основанный в 1966 году. 



В коллекцию входят:
- [Чарт подкастов на Яндекс-музыке](https://music.yandex.ru/chart/podcasts)
- [Стартовая страница подкастов Google](https://podcasts.google.com/) (за неимением онлайн-чарта в Google подкастах)
- [Чарт топ-подкастов castbox.fm](https://castbox.fm/categories/0?country=ru) по региону Россия
- [Аналитика/чарт топ-подкастов Apple music с портала Chartable](https://chartable.com/charts/itunes/ru-all-podcasts-podcasts) (чарты Apple music доступны в открытом доступе но только в приложении на macos/ios)
- [Чарт топ-подкастов Deezer.com](https://www.deezer.com/en/channels/russian-speaking) по подвыборке русскоязычных подкастов (можно заметить что выборка определена неточно и большинство подкастов в чарте не на русском языке)
- [Стартовая страница zvuk.com](https://zvuk.com/podcasts) (за неимением онлай-чарта в открытом доступе)

Более подробное описание коллекции, а также описание ход работы по загрузке архивов через `wpull` можно найти [в файле по ссылке](./pdf-reports/summary_and_wpull_archiving.pdf) 
Подробное описание анализа коллекции в `ArchiveReady` по метрикам CLEAR доступно [в файле по ссылке](./pdf-reports/summary_ArchiveReady_analysis.pdf) 

## Метод и технология

В данной работе мы использовали несколько инструментов для создания полноценной коллекции веб-архивов.

1. Для сохранения архива мы воспользовались `wpull`. Этот инструмент представляет из себя утилиту командной строки а также библиотеку `Python` и позволяет загружать архивы с широким выбором заданных параметром (глубина рекурсии, timeout, метаданные архивирующего лица итд). В данной работе для загрузки нескольких архивов последовательно, мы воспользовались `wpull` через `Python`-скрипт массовой загрузки

2. Воспроизвести полученные архивы удалось с помощью сервиса [ReplayWeb.page](https://replayweb.page/),

3. Для каждого архива мы проанаизировали качество полученных материалов с помощью инструмента [ArchiveReady](https://archiveready.com/),

4. Наконец, для каждого архива мы произвели анализ метаданных с помощью `Python`-библиотеки `metawarc`


## Описания работы по каждому веб-архиву и структура репозитория
1. **archives/**
   - **apple-music-chartable.com/**
     - **README.md**: Ход работы по архивированию с `wpull`, анализа CLEAR метрик в `ArchiveReady`, анализ метаданных в `metawarc` для подкастов в Apple Music в аггрегаторе аналитики chartable.com.
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
   - **castbox.fm/**
     - **README.md**: Ход работы (`wpull`,`ArchiveReady`, `metawarc`) для сайта castbox.fm
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
   - **deezer.com/**
     - **README.md**: Ход работы (`wpull`,`ArchiveReady`, `metawarc`) для сайта DEEZER
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
   - **music.yandex.ru/**
     - **README.md**: Ход работы (`wpull`,`ArchiveReady`, `metawarc`) для Яндекс музыки
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
   - **podcasts.google.co/**
     - **README.md**: Ход работы (`wpull`,`ArchiveReady`, `metawarc`) для подкастов Google
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
   - **zvuk.com/**
     - **README.md**: Ход работы (`wpull`,`ArchiveReady`, `metawarc`) для сайта zvuk.com
     - **digital_meta.jsonl**: Файл с подсчетом метаданных.
     - ...
2. **pdf-reports/**
   - **summary_and_wpull_archiving.pdf** подробное описание работы по сохранению архивов коллекции с помощью `wpull`
   - **summary_ArchiveReady_analysis.pdf** подробное описание работы по анализу сайтов коллекции на портале `ArchiveReady` по метрикам `CLEAR` 

## Итог работы
В ходе работы мы занимались созданием коллекции русскоязычных подкастов, обращая внимание на технические аспекты архивации и анализа данных. Важным результатом работы стало понимание сложности создания коллекции из различных ресурсов и выявление технических вызовов, таких как неполные данные и технические сбои при архивировании. Кроме того, необходимость корректировки оценки архивации в зависимости от конкретной задачи выделяет важность формулировки требований и целей перед началом работы с архивами.

Таким образом, выполненная работа не только обогатила наши знания в области архивации и в предметной DH-области, но также подчеркнула важность внимательного подхода к выбору ресурсов, постановке задачи и оценке результатов.

## Контакты
[Горбачев Николай](https://github.com/n1kg0r), 
ЦМГН ВШЭ,
2023

## Условия использования 
<p xmlns:cc="http://creativecommons.org/ns#" >Данная работа может свободно распространяться по лицензиии <a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC0 1.0 Universal<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/zero.svg?ref=chooser-v1"></a></p>
