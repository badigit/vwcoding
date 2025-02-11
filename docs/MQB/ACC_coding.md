disqus: https-mqb-readthedocs-io
# Адаптивный круиз контроль. Кодирование

### Разрешить обгон/опережение справа для Адаптивного Круиз Контроля (АСС)

!!! tip ""
    По умолчанию система ACC тормозит автомобиль, если на полосе слева едет медленный автомобиль (даже при пустой дороге).

=== "Кодирование в ODIS"
    ```
    Блок 13 → Кодирование
    > Overtaking_right_prevention (Vermeidung für unzulässigen Überholvorgang)
    > Установить Deactivated [Default: Activated]
    → Применить
    ```
=== "Кодирование в OBD11"
    ```
    Блок 13 (Адаптивный круиз контроль) → Безопасный доступ → Логин-пароль 20103
    > Длинное кодирование
    > Overtaking_right_prevention → Установить Deactivated [Default: Activated]
    → Применить
    ```
=== "Кодирование в VCDS" 
    ```
    13 Блок Adaptive Cruise Control  
    2 Байт → 5 Бит: Overtaking_right_prevention - выключить  
    Выход   
    Сохранить
    ```   
    ![Screenshot](../images/MQB/overtake.png)

> логин-пароль 20103
   
### Активация выбора режима работы Адаптивного Круиз Контроля (АСС), независимо от выбранного Профиля езды

=== "Кодирование в ODIS"
    ```
    Блок 13 → Кодирование
    > Drive_pmode_selection - Меню MMI Адаптивный круиз контроль (ACC)
    → Применить
    ```
=== "Кодирование в VCDS" 
    ```
    13 Блок Adaptive Cruise Control  
    Кодирование - 07 → Длинное кодирование  
    Байт 3 → бит 7: Drive_pmode_selection, 0=MMI menu ACC / 1=Driving profile selection → снимаем галочку  
    Выход    
    Сохранить
    ``` 
    ![Screenshot](../images/MQB/acc.png)

> логин-пароль 20103 

### Увеличение времени ожидания трогания Адаптивного Круиз Контроля (АСС)

По умолчанию система Stop & Go после полной остановки активна только 3 секунды. По истечении этого времени продолжить движение можно только кнопкой на руке, либо педалью акселератора.  

Снять это ограничение невозможно, однако на последних версиях прошивки можно увеличить временной интервал до 10 секунд.  

Требования к прошивкам:  
```
3QF907561, 5Q0907561 - SW 0780, H10-H11  
2Q0907561, 2Q0907572 - SW 0383, H01-H04
```

```
Блок 13 → Кодирование  
> Байт 11 - бит 0: Pretriggertime_reduction - деактивировать  
→ Применить
```

### Регулировка толерантности (только для 5Q0 радаров)

![Screenshot](../images/MQB/pacc_offset.jpeg)  

Пункт меню «Учитывать допустимую скорость» и непосредственно включает или выключает режим регулирования скорости АСС в зависимости от знаков в навигации или распознанных камерой.
```
Блок 13 → Кодирование  
> Tempolimitassistent_CarMenu — активировать
```

Пункт настроек допустимых отклонений в меню «Адаптивного Круиз Контроля»
```
Блок 13 → Кодирование  
> zul_Regelabweichung_CarMenu — large
```

Выставленные Вами для того или иного знака ограничения будут сохраняться и автоматически подставляться каждый раз при распознавании этих знаков.
```
Блок 13 → Кодирование  
> pACC_Learning_drivers_offset — activated
```

### Настройка предупреждения Front Assist
```
Блок 13 → Кодирование  
> adjustability_awv_pre_warning — деактивировать
> default_value_awv_pre_warning — активировать
```
