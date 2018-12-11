### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Kalendarz perski korzysta z algorytmu słonecznego Hidżry

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> klasy używa algorytmu słonecznego Hidżry. Konwertowanie daty wypadające między <xref:System.Globalization.PersianCalendar?displayProperty=name> i innych kalendarzy może zwrócić wynik nieco zaczyna się od programu .NET Framework 4.6 daty wcześniejszej niż 1800 lub późniejsza niż 2023 (gregoriańskiego). Ponadto <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest teraz <code>March 22, 0622</code> zamiast <code>March 21, 0622</code>.|
|Sugestia|Należy pamiętać, że niektóre daty wczesne i późne mogą być nieco inne w przypadku korzystania z PersianCalendar w .NET Framework 4.6. Ponadto podczas serializowania dat między procesami, które mogą być uruchamiane w innej wersji programu .NET Framework, nie należy przechowywać je jako ciągi daty z PersianCalendar (ponieważ te wartości mogą się różnić).|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

