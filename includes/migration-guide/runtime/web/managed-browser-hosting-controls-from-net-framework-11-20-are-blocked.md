### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Kontrolki hostingu programu Managed browser z .NET Framework 1.1 i 2.0 są zablokowane.

|   |   |
|---|---|
|Szczegóły|Obsługa tych formantów jest zablokowana w programie Internet Explorer.|
|Sugestia|Program Internet Explorer nie będzie mógł uruchomić aplikacji, która używa formantów zarządzanego hostingu w przeglądarce. Poprzednie zachowanie można przywrócić, ustawiając wartość EnableIEHosting podklucza rejestru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> do <code>1</code> dla x86 systemów i procesów 32-bitowych w x64 systemów i ustawiając <code>EnableIEHosting</code> wartość podklucza rejestru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>do <code>1</code> dla procesów 64-bitowego na x64 systemów.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

