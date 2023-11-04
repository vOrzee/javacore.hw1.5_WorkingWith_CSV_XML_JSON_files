# Домашнее задание к занятию 1.5: Работа с файлами CSV, XML, JSON

Необходимо выполнить и предоставить на проверку следующие задачи:

1. [CSV - JSON парсер](https://github.com/vOrzee/javacore.hw1.5_WorkingWith_CSV_XML_JSON_files/tree/task1.CSV-JSON-parser#%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B0-1-csv---json-%D0%BF%D0%B0%D1%80%D1%81%D0%B5%D1%80);
2. ***XML - JSON парсер***;
3. [JSON парсер](https://github.com/vOrzee/javacore.hw1.5_WorkingWith_CSV_XML_JSON_files/tree/task3.JSON-parser#%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B0-3-json-%D0%BF%D0%B0%D1%80%D1%81%D0%B5%D1%80-%D1%81%D0%BE-%D0%B7%D0%B2%D0%B5%D0%B7%D0%B4%D0%BE%D1%87%D0%BA%D0%BE%D0%B9-) (задание со звездочкой *).

# Задача 2: XML - JSON парсер

## Описание
В данной задаче вам предстоит произвести запись в файл JSON объекта, полученного из XML файла.

Данную задачу выполняйте в рамках созданного в предыдущей задаче проекта.

В качестве исходной информации создайте файл `data.xml` со следующим содержимым (поместите этот файл в корень проекта):
```xml
<staff>
    <employee>
        <id>1</id>
        <firstName>John</firstName>
        <lastName>Smith</lastName>
        <country>USA</country>
        <age>25</age>
    </employee>
    <employee>
        <id>2</id>
        <firstName>Inav</firstName>
        <lastName>Petrov</lastName>
        <country>RU</country>
        <age>23</age>
    </employee>
</staff>
```
В резyльтате работы программы в корне проекта должен появиться файл `data2.json` с содержимым, аналогичным json-файлу из предыдущей задачи.

## Реализация
Для получения списка сотрудников из XML документа используйте метод `parseXML()`:
```java
List<Employee> list = parseXML("data.xml");
```
При реализации метода `parseXML()` вам необходимо получить экземпляр класса `Document` с использованием `DocumentBuilderFactory` и `DocumentBuilder` через метод `parse()`. Далее получите из объекта `Document` корневой узел `Node` с помощью метода `getDocumentElement()`. Из корневого узла извлеките список узлов `NodeList` с помощью метода `getChildNodes()`. Пройдитесь по списку узлов и получите из каждого из них `Element`. У элементов получите значения, с помощью которых создайте экземпляр класса `Employee`. Так как элементов может быть несколько, организуйте всю работу в цикле. Метод `parseXML()` должен возвращать список сотрудников.

С помощью ранее написанного метода `listToJson()` преобразуйте список в JSON и запишите его в файл c помощью метода `writeString()`.
