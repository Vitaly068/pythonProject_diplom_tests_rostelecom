Тестирование авторизации в ЛК "Ростелеком" 

Требования описаны в брифе от заказчика https://docs.yandex.ru/docs/view?url=ya-browser%3A%2F%2F4DT1uXEPRrJRXlUFoewruJzxAhMByh6BlVLEbpwoMTCn6rGc72aRF9lZK0LT0NE-B9DW15pqEDKmwqId-lkaZrHn6S3n7lc7zdGFlVuKrjt_nsdRpDgBflNTQyd7XKMg62uNE-6XJ7oH0X_Z4Byhbw%3D%3D%3Fsign%3DfDgYAkrAAq1Cksnz1ZDE9hIL1sbhP-zCNXR8_ZJdD4w%3D&name=asset-v1_SkillFactory%2BQAP-3.0%2B2021%2Btype%40asset%2Bblock%40Требования_SSO_для_тестирования_last.doc&nosw=1

Реализованы тесты к "Стандартная авторизация по логину и паролю"

План тестирования [https://docs.google.com/document/d/1tkv6cTe2qniEKuxTrLpofAwYVcvDWVfMjJLlJxMGsLc/edit?usp=sharing](https://docs.google.com/document/d/1TnuROizSxGJLTlnc3E8hNmCRPGoSbnsp/edit?usp=sharing&ouid=111247672046941453128&rtpof=true&sd=true)

Тест-кейсы [https://docs.google.com/spreadsheets/d/11tG22XI9HXs96GlXEyA3smjUgB46q2JCDjfGDWcZB1k/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1FYetGkz-zWhuYDVDXK087zKMzPQxk6Zr/edit?usp=sharing&ouid=111247672046941453128&rtpof=true&sd=true)
На вкладке "Форма авторизации" описаны тест-кейсы по проверке наличия на странице авторизации всех описанных в требованиях элементов
На вкладке "Авторизация" описаны тест-кейсы по авторизации в ЛК Ростелеком
Найденные баги описаны на вкладке "Баги" в документе с тест-кейсами

При создании тест-кейсов использованы техники позитивного тестирования для проверки авторизации на сайте различными способами, описанными в технических требованиях, и негативного тестирования для проверки невозможности доступа в личный кабинет с неподходящими данными и оповещения пользователя об ошибке доступа. В негативном тестировании используются классы эквивалентности для подбора вариантов данных для тестов.

При проведении тестов возможно появление капчи в форме авторизации. В этом случае сразу после ввода данных в полях логин и пароль нужно кликнуть в поле ввода капчи и за 20 сек. ввести текст с картинки. Если не успеть это сделать, тест будет провален.

Негативные тесты на авторизацию с пустым паролем отмечены как xfail, т.к. все время падают - на сайте нет предупреждения о вводе пароля.


Инструменты, которые применялись для тестирования:
Для тестирования сайта был использован интсрумент Selenium;
Для определения локаторов использовались следующие инструменты: DevTools, ChroPath.
Запуск тестов:
python -m pytest -v --driver Chrome --driver-path //Driver/chromedriver.exe tests/test_auth_page_elements.py
python -m pytest -v --driver Chrome --driver-path //Driver/chromedriver.exe tests/test_negative_auth.py
python -m pytest -v --driver Chrome --driver-path //Driver/chromedriver.exe tests/test_positive_auth.py
