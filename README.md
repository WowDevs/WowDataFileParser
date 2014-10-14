WowDataFileParser
=================

Описание файла
 * name  - Имя файла, для которого указана структура

Описание столбцов:
 * name     - Наименование столбца, если имя пустое - тогда данные не будут записаны в базу данных.
              Важно: Если на этот столбец будет ссылатся другое поле "size" - тогда имя должно быть указано.
 * key      - Указывает, что поле является ключевым (необходим для генерации sql скрипта с таблицами)
 * size     - Размер поля в битах или имя поля содержащее размер.
 * maxsize  - Mаксимальный размер списка (обязательный параметр для type == list)
 
 * type     - Тип данных:
    * byte    - 8  byte и size - количество бит
    * short   - 16 byte и size - количество бит
    * ushort  - 16 byte и size - количество бит
    * int     - 32 byte и size - количество бит
    * uint    - 32 byte и size - количество бит
    * long    - 64 byte и size - количество бит
    * ulong   - 64 byte и size - количество бит
    * float   - 32 с плавающей запятой
    * double  - 64 с плавающей запятой

    * string  - строка с '\0' окончанием.
                если строка содержит аттрибут size (строка)- тогда длинна строки содержится в указанном поле.
                если строка содержит аттрибут size (число) - тогда читается строка с указанной длинной.
    * string2 - то же самое что и string, только читаются данные если (size) > 1

    * pstring - (pascalstring) строка которая содержит длинну в начале,
                обязательный параметр size - в котором указн размер записи с длинной в битах

    * list    - тип данных который сожержит вложенную структуру.
                для этого типа обязательный аттрибут maxsize.
                Если указан только maxsize - тогда это список с постоянной длиной.
                атрибут size (число)  - тогда сначала считывается размер списка (указывается в битах).
                атрибут size (строка) - ссылка на поле с размером списка.
