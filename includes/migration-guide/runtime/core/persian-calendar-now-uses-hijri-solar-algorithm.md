### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perska kalendarza teraz używa algorytmu słonecznego Hijri

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> klasy używa algorytmu słonecznego Hijri. Konwertowanie daty wypadające między <xref:System.Globalization.PersianCalendar?displayProperty=name> i innych kalendarzy mogą być nieco różne wyniki, począwszy od programu .NET Framework 4.6 dat wcześniejszych od 1800 lub nowszej niż 2023 (gregoriański). Ponadto <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest teraz <code>March 22, 0622</code> zamiast <code>March 21, 0622</code>.|
|Sugestia|Należy pamiętać, że niektóre dat wczesne i późne mogą być nieco inne w przypadku korzystania z PersianCalendar w .NET Framework 4.6. Ponadto podczas serializowania dat między procesami, które mogą być uruchamiane na różne wersje programu .NET Framework, nie należy przechowywać je jako ciągi daty PersianCalendar (ponieważ te wartości mogą się różnić).|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

