# Отчёт о тестировании OpenJDK11 на ОС Windows 10

## Краткое описание

В рамках тестирования было проверено:

* Инструкция по установке OpenJDK11 работает под ОС Windows 10
* Приложение запускается и совместимо с Java 11
* Приложение работает согласно [руководству использования](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/user-manual.md)

Дата начала 25.03.2020 - Дата окончания 25.03.2020 было проведено тестирование установки приложения OpenJDK11.

На тестирование затрачено: 10 минут

В результате тестирования выявлены следующие дефекты:
* [Валидный ключ KeyValidator отдает FAIL](https://github.com/voevodina/introduction/issues/1)
* [Невалидный ключ KeyValidator отдает OK](https://github.com/voevodina/introduction/issues/2)

## Описание процесса тестирования

В процессе тестирования использовались следующие артефакты*:
* [Инструкция по установке OpenJDK11](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/openjdk11-manual.md)
* [Руководство использования KeyValidator](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/user-manual.md)

В качестве тестовых данных использовались данные из [Руководства использования KeyValidator](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/user-manual.md) и [Инструкции по установке OpenJDK11](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/openjdk11-manual.md):

* Установочный файл **OpenJDK11U-jdk_x64_windows_hotspot_11.0.6_10.msi** с сайта [adoptopenjdk.net](https://adoptopenjdk.net/)
* [Приложение KeyValidator в виде файла](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/artifacts/KeyValidator.class)

* **Валидные ключи** :

    * 8f05e6a7-70e9-33d7-bfe7-b19eae0d8998
    * 80b427f8-92cd-3aae-ba04-3927fbe17c6
    * b295bc63-9f03-3b4b-af80-969b39f8c262
    * 387eedc6-12e9-3b32-9881-63b6b5e85317
    * c19a8cf9-5c3a-37c5-b7f3-d16d38a0c180
    
* **Невалидные ключи** :

    * 18252235-78e0-44a5-8720-556f0c7da17a
    * e66075b6-ddad-445e-baf6-161b3289522b
    * b6d53250-f07e-4352-a293-6102ddf7f1ca
    * c2bc778a-1cb9-46c6-b435-0489649d2a42
    * 2fb98b44-93e7-3bdd-a2ad-79347bfe4ad1
 
>Шаг 1. Перейдите на сайт adoptopenjdk.net. 

    ОК
    
>Шаг 2. Выберите опции как на скриншоте ниже и нажмите на кнопку скачивания:

    ОК

>Шаг 4. Прочитайте и согласитесь с условиями лицензии:

    ОК

>Шаг 5. Выберите опции как на экране (удостоверьтесь, что установка происходит в Program Files и опция Add to PATH выбрана):
    
    ОК

>Шаг 6. Нажмите на кнопку "Install":

    ОК

>Шаг 7. Дождитесь окончания установки и нажмите на кнопку "Finish":

    ОК

>Откройте терминал и выполните команду java -version. 

**Ожидаемый результат**:

        openjdk version "11.0.5" 2019-10-15
        OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.5+10)
        OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.5+10, mixed mode)

**Фактический результат** соответствует ожидаемому:

![Java-version](https://github.com/voevodina/images/blob/master/java_version.png)

После успешной установки приложения был произведен запуск файла [KeyValidator](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/artifacts/KeyValidator.class) в терминале Git Bush Here.

>Шаг 1. Ввела в терминале команду java KeyValidator 00000000-0000-0000-0000-000000000000 00000000-0000-0000-0000-000000000001 

*где 00000000-0000-0000-0000-000000000000, 00000000-0000-0000-0000-000000000001 - передаваемые для валидации ключи из тестовых данных*

**Ожидаемый результат**:

    Result for 00000000-0000-0000-0000-000000000000: OK
    Result for 00000000-0000-0000-0000-000000000001: FAIL


*где OK означает, что ключ валидный, FAIL - невалидный.*    

**Фактический результат** :

Часть ключей из списка валидных отдают FAIL, что не соответствует ожидаемому результату.

Часть ключей из списка невалидных отдают ОК, что не соответствует ожидаемому результату.

![Keys](https://github.com/voevodina/images/blob/master/keys.png)

Тестирование производилось в следующем окружении:

* ОС Windows 10 Pro, 64bit
* версия Java 11
