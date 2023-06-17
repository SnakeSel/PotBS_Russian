# Корсары Онлайн: Pirates of the burning sea.
### Russian language

Актуальный перевод PotBS для *Live* серверов.
```
ru_ru_data.dat и ru_ru_data.dir - Файлы Русского перевода.
PotBS_lang - утилита для создания ".dir" файла из ".dat".
```
### Для установки в игру:
1. Скачайте *ru_ru_data.dat* и *ru_ru_data.dir*
2. Поместите файлы *ru_ru_data.dat* и *ru_ru_data.dir* в папку PotBS/locale

### Для самостоятельного перевода:
1. Скачайте *ru_ru_data.dat* и *en_us_data.dat*
2. Переведите строки из *en_us_data.dat* которых нет в *ru_ru_data.dat* и запишите их в *ru_ru_data.dat*
3. Скачайте *PotbS_lang_x64.exe* (для Windows) или *PotbS_lang_x64* (для Linux)
4. Запустите *PotbS_lang_x64.exe* указав имя файла ru_ru_data.dat: `PotbS_lang_x64.exe ru_ru_data.dat`
5. Поместите файлы *ru_ru_data.dat* и *ru_ru_data.dir* в папку PotBS/locale

Можете попробовать [графическую программу](https://github.com/SnakeSel/PotBS_LangUI) для перевода.

### Заметки по переводу:
* Строка с переводом должна заканчиваться переносом строки в стиле Windows (`\r\n`).
* Если нужно перейти на новую строку внутри перевода, пишем `\n`.  
  Пример: `Используйте колесико\nдля приближения\nи отдаления`.
* В `[! ... !]` указываются макросы. Их переводить не нужно.
* Чтобы слово начиналось:
  * с *Б*ольшой буквы, оберните его в макрос `#cap()`
  * с *м*аленькой буквы, оберните его в макрос `#uncap()`
* О ошибках в переводе сообщайте в Discord: `SnakeSel#3818` или на email: `snake.sel@gmail.com`


#### Перевод в зависимости от пола
Указывается с помощью:
* Общий: *#m("...")* и *#f("...")*  
  Пример: `Никогда не #m("встречал")#f("встречала")` или `Все бы отдал#f("а")`.
* Пол говорящего: #ms() и #fs() `я #ms("уверен") #fs("уверена")`
* Пол собеседника: #ml() и #fl() `#ml("мой мальчик") #fl("моя девочка").`  
  Пример: `Я в значительной степени #ms("уверен") #fs("уверена"), что это наше, а не ваше, #ml("мой мальчик") #fl("моя девочка").`


#### Склонение по падежам
В игре используются следующие падежи:

| Название        | Падеж        | Отвечает на вопросы | В переводе | В макросе |
| --------------- | ------------ | ------------------- | ---------- | --------- |
| Nominativus     | Именительный | Кто? Что?           | {nm}       | #nom()    |
| Genetivus       | Родительный  | Кого? Чего?         | {gs=""}    | #gen()    |
| Dativus         | Дательный    | Кому? Чему?         | {ds=""}    | #dat()    |
| Accusativus     | Винительный  | Кого? Что?          | {as=""}    | #acc()    |
| Instrumentalis  | Творительный | Кем? Чем?           | {is=""}    | #inst()   |
|                 | Предложный   | О ком? О чём?       | {ps=""}    | #prep()   |
|		  |		 |		       | {pl=""}    |           |

Для склонения по падежам необходимо сначала перевести слово с указанием падежей, а потом использовать макрос отвечающий за слово с указанием падежа.

1. Переводим слово. Самое сложное найти то слово за которое отвечает нужный макрос. Только методом тыка.
Для склонения по падежам используйте: *{nm}..{gs="..", ds="..", as="..", is="..", ps=".."}*.  
  Пример: `{nm}здоровье{gs="здоровья", ds="здоровью", as="здоровья", is="здоровьем", ps="здоровье"}`  
Если слово не склоняется, но в макросе стоит использование падежа (для других слов), то перед словом нужно поставить *{nmx}* или *{nfx}*
  Пример: `{nmx}Аледо`
2. Для использования нужного падежа, "оборачиваем" макрос в нужный падеж: *#nom(), #gen(), #dat(), #acc(), #inst(), #prep()*  
  Пример: `[!ATTACKER!] бьет #acc([!TARGET!]), нанося [!DAMAGE!]  ед. урона #dat([!DAMAGE_TYPE!]).`

