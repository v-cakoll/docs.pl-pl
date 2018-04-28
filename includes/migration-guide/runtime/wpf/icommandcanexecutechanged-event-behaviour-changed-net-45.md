### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>Zachowanie zdarzenia ICommand.CanExecuteChanged zmienione w programie .NET 4.5

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> został zignorowany, chyba że nadawca zdarzenia był ten sam obiekt jako obiekt, który wywołał zdarzenie. Ten problem został rozwiązany w programie .NET Framework 4.5 aktualizacji obsługi.|
|Sugestia|Ten problem został rozwiązany w programie .NET Framework 4.5 obsługi wersji, więc można uniknąć, upewniając się, że programu .NET Framework jest aktualny, albo przez uaktualnienie .NET Framework 4.5.1. Alternatywnie kodu aplikacji za pomocą <xref:System.Windows.Input.ICommand?displayProperty=name> można zmodyfikować, aby upewnić się, że nadawca podczas podnoszenia <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> polecenia jest taki sam, jak dla obiektu wywołaniem zdarzenia.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|Analizatory|<ul><li>CD0084</li></ul>|

