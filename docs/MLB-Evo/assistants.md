disqus: https-mqb-readthedocs-io
# Активация ассистентов

### Активация Line Assist

!!! warning ""
    Для активации данного ассистента не нужна параметрия

```
Блок A5 (камера ассистентов) → Кодирование 
> ALDW_lane_assist - установлено
→ Применить
```

> логин-пароль 20103

Включаем в меню новые функции
```    
Блок 5F (мультимедия) → Адаптация 
> Car_Function_List_BAP_Gen2
>> LDW_HCA_0x19: activated
>> LDW_HCA_0x19_msg_bus: Terminal 15
> Car_Function_Adaptations_Gen2
>> menu_display_Lane_Departure_Warning: activated;
>> menu_display_Lane_Departure_Warning_over_threshold_high: activated;
→ Применить 
```

HCA - Указание блоку рулевого управления о наличии Line Assist
```
Блок 44 (усилитель рулевого) → Кодирование
Ассистент движения по полосе, связ. с усилителем рул. управления
> Heading Control Assistant: active
 (Байт 03 - бит 1 → активировать (heading_control_assist: not active → active))
→ Применить 
```

```
Блок 09 (бортовая сеть) → Адаптации
>> Heading Control config → heading_control
→ Применить 
```

> логин-пароль 20103

Включаем отображение Line Assist на приборной панели
```
Блок 17 (комбинация приборов/ActiveInfoDisplay)  → Кодирование
> Lane_assist: yes
→ Применить 
```

```
Блок A5 (камера ассистентов) → Адаптация 
> Lane_departure_warning_on_state → Selection_over_menu_default_on
→ Применить 
> Personalisation_for_lane_departure_warning
>> TT_activated_not_activated → activated изменить на last_setting
→ Применить 
```

### Активация ассистента дорожных знаков (автомобиль должен быть оснащен камерой)

!!! warning ""
    Для активации данного ассистента может потребоваться параметрия

Автомобильная камера будет считывать дорожные знаки и отображать заданную скорость в кластере.

```    
Блок 5F (мультимедия) → Адаптация 
> Vehicle function list BAP
>> traffic_sign_recognition_0x21: activated
> Vehicle menu operation
>> menu_display_road_sign_identification: activated
>> menu_display_road_sign_identification_over_threshold_high: activated
→ Применить 
```
```
Блок A5 (камера ассистентов) → Кодирование 
> Байт 1 - Бит 0 (Traffic Sign Recognition (FTE) active) - установлено
→ Применить
```
> логин-пароль 20103

```
Блок 17 (комбинация приборов/ActiveInfoDisplay)  → Кодирование
> Байт 5 - Бит 2 → активировать
→ Применить 
```
```
Блок A5 (камера ассистентов) → Адаптация 
> Select : channel numbers indicate end of speed limit
Importance to actively invest Show Valid suffix
View Channel Valid suffix
Corresponding value adjust default: 00100111
→ Применить 
```
> логин-пароль 20103

### Активация Emergency ассистента

!!! warning ""
    Для активации данного ассистента может потребоваться параметрия
    
```
Блок A5 (камера ассистентов) → Адаптация 
> EA_emergency_assist → Variant_2
→ Применить 
```
> логин-пароль 20103

```
Блок 13 (Адаптивный круиз-контроль) → Кодирование 
> Emergency_steer_assist → activated
→ Применить 
```
```
Блок 46 (Центральный модуль систем комфорта) → Кодирование 
> central_locking_system_emergency_assist → active
→ Применить 
```

### Отображение ассистентов на проекции на лобовое стекло
:octicons-verified-24: Audi
```
Блок 82 → Кодирование
> Road sign detection: not available → available (отображение дорожных знаков)
> Lane Departure Warning: not available → available (отображение Lane Assist)
→ Применить 
```