# rnn_things
## Скриптик для обучения и генерации текста рекурентными сетями

Код взят из статьи на Хабре: https://habr.com/ru/articles/470035/
Доработан Хачирукой 

## Поддерживаемые параметры запуска:
* '[-t --text]'          Путь к файлу с информацией для обучения 
* '[-e --epoch]'         Количество эпох обучения 
* '[-p --phrase_len]'    Глубина анализа текста (Чтобы это не значило -_-) 
* '[-m --model]'         Путь к уже обученной модели 
* '[-v --vocab_size]'    Число, выдающееся при обучении, необходимое для звпуска модели без тренировачних данных 
* '[-g --generate]'      Параметр запуска генерации текста с ипользованием готовой модели 
* '[-s --seed]'          Начальная фраза, дающаяся сети для её последующего продолжения 

## Особенности использования скрипта: 
* При обучении вам будет выдан vocab_size вашей модели, он зависит от ваших данных для обучения модели и генерируется из них же 
vocab_size необходим при запуске модели без доступа к данным обучения, поэтому необходимо его запомнить или записать куда-нибудь 

* Сохранение модели произходит автоматически после каждой эпохи, новая модель будет сразу же заменять старую без создания "ранних версий" 
Модели сохраняются с тем же названием что и название вашего файла с данными обучения, за исключением замены .txt на .keras 

* Могу дать совет по построению данных для обучения - так как сеть пытается предугадать, какой символ будет идти следующим, 
в выборке вам необходимо иметь осмысленные строки текста (Код, диалоги, стихи, научные статьи и т.д.) От того как ваши данные 
построенны зависит вызод сети. 
 
* Стоит отметить что сеть будет пародировать стиль написания из обучающих данных, так если это был какой либо код, то сеть при 
должном количестве обучения будет в какой-то степени соблюдать строение этого кода, или если это будет набор из строк с одним 
словом на каждой из них, то сеть будет выдавать аналогично отформатированый результат. 

* Внутри файла так же есть переменные, которые нельзя изменить при помощи консольных параметров ввиду структуры кода и моей лени. 
Если вам необходима более тчательная настройка сети - милости прошу редактировать код. 
