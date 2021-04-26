
# Comandos sincronizar as datas e horas de Windows e Linux dual boot

Abra um terminal e desative o UTC e use a Hora Local no Ubuntu:

```
timedatectl set-local-rtc 1 --adjust-system-clock
```

Depois para confirmar basta digitar:

```
timedatectl
```

A saída será:

```
               Local time: seg 2021-04-26 07:00:52 -04
           Universal time: seg 2021-04-26 11:00:52 UTC
                 RTC time: seg 2021-04-26 07:00:52    
                Time zone: America/Cuiaba (-04, -0400)
System clock synchronized: yes                        
              NTP service: active                     
          RTC in local TZ: yes                        

Warning: The system is configured to read the RTC time in the local time zone.
         This mode cannot be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.
```

O importante na saída é ter o Warning avisando que o RTC está como local

