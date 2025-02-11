disqus: https-mqb-readthedocs-io
# Звук

### Улучшение звучания

!!! tip ""
    Данная настройка меняет звучание магнитолы очень посредственно.   
    Для более качественного звучания необходимо загружать параметрию в блок.

=== "Кодирование в ODIS"   
    ```
    Блок 5F → Кодирование
    > byte_11_Sound_System
    Выбираем Sound_System_no_Allocation или Sound_System_Internal 
    → Применить (с перезагрузкой блока)
    ```

=== "Кодирование в OBD11"
    ```
    5F - MMI / RNS  
    Кодирование - 07 → Длинное кодирование  
    Байт 11 → Выбираем Sound_System_no_Allocation или Sound_System_Internal либо  
    заменить 01 бит на 04 бит  
    Выход  
    Сохранить  
    ```

> логин-пароль 20103 

### Повышение чувствительности микрофона

!!! tip ""
    Речь водителя при звонке из автомобиля стало слышно четче. Диапазон регулировки от -10 до 10. Самые оптимальные значения идут от 2-х

=== "Кодирование в ODIS"
    ```
    Блок 5F → Адаптация
    > Microfone sensivity (Mikrofonempfindlichtkeit)
    > От 2-х до 10Db
    → Применить 
    ```

=== "Кодирование в OBD11" 
    ```
    5F Блок Электронная информационная система → Адаптация  
    > Чувствительность микрофона  
    Старое значение: 0 Дб  
    Новое значение: 2-10 Дб
    ```
    
> логин-пароль 20103     