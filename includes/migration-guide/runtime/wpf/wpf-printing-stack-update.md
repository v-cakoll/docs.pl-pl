### <a name="wpf-printing-stack-update"></a>Aktualizacja stosu drukowanie WPF

|   |   |
|---|---|
|Szczegóły|Przy użyciu drukowanie interfejsów API firmy WPF <xref:System.Printing.PrintQueue?displayProperty=name> teraz wywołać interfejs API pakietu dokument Drukuj okna na rzecz teraz przestarzałe API drukowania XPS. Zmieniono z użytkowanie pamiętać; Deweloperzy ani użytkowników powinny być widoczne wszelkie zmiany zachowania lub użycia interfejsu API. Nowe drukowania jest domyślnie włączona, podczas uruchamiania w systemie Windows 10 twórców aktualizacji. Stary stosu drukowania będą nadal działać tak jak poprzednio w starszych wersjach systemu Windows.|
|Sugestia|Aby użyć starego stosu w systemie Windows 10 twórców aktualizacji, należy ustawić <code>UseXpsOMPrinting</code> wartości REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klucz rejestru w celu <code>1</code>.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|środowisko uruchomieniowe|

