### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy teraz zwraca nową kopię zamiast bieżące wystąpienie

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> zwrócił odwołanie do bieżącego wystąpienia, przede wszystkim jako optymalizacji wydajności. W programie .NET Framework 4.5 zwraca nowe wystąpienie, dzięki czemu można stwierdzić, że równy odwołania wskazująca, że wykonywania wątek znajduje się w kontekście synchronizacji poprawne po raz pierwszy.  Jest mało prawdopodobne, że będzie dotyczył kodu, który sprawdza tożsamość te odwołania, ale z powodu zmiany kodu tego wywołania <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> powinny być testowane w ramach migracji do programu .NET Framework 4.5 lub nowszej.|
|Sugestia|Należy pamiętać, że <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> teraz zwróci nowy <xref:System.Threading.SynchronizationContext?displayProperty=name> obiektu. Wcześniej kod, którego równoważność generowane w ten sposób odwołania został nie faktycznie sprawdza czy go w kontekście prawidłowego, ale nie w przypadku skompilowany dla platformy .NET Framework 4.5 lub nowszej.  Podczas, gdy jest to prawdopodobnie nie będzie powodować problemy, wykonywania ścieżek kodu powinny wystarczyć do ustalenia, czy stanowi to problem.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|

