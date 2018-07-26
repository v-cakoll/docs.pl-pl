### <a name="wpf-printing-stack-update"></a>Aktualizację stosu drukowanie WPF

|   |   |
|---|---|
|Szczegóły|Za pomocą drukowanie interfejsów API firmy WPF <xref:System.Printing.PrintQueue?displayProperty=name> teraz wywołania interfejsu API pakietu dokument Drukuj okna na rzecz teraz przestarzałe API drukowanie plików XPS. Zmiana została wprowadzona przy użyciu użytkowanie pamiętać; Użytkownicy ani deweloperzy nie powinny zostać wyświetlone wszelkie zmiany w zachowanie lub użycie interfejsu API. Nowy stos drukowania jest domyślnie włączona, podczas uruchamiania w systemie Windows 10 Creators Update. Stary stosu drukowania będą nadal działać tak jak wcześniej w starszych wersjach Windows.|
|Sugestia|Aby użyć starego stosu w aktualizacji systemu Windows 10 dla twórców, ustaw <code>UseXpsOMPrinting</code> wartości REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klucza rejestru w celu <code>1</code>.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

