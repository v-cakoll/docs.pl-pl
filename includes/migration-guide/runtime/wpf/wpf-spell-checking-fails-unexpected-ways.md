### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Sprawdzanie pisowni WPF nie powiedzie się w nieoczekiwany sposób

|   |   |
|---|---|
|Szczegóły|Obejmuje to wiele problemów WPF moduł sprawdzania pisowni:<ul><li>Czasami zgłasza sprawdzania pisowni WPF <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Moduł sprawdzania pisowni WPF kończy się niepowodzeniem z <xref:System.UnauthorizedAccessException> podczas uruchamiania aplikacji za pomocą polecenia "Uruchom jako inny użytkownik"</li><li>Moduł sprawdzania pisowni WPF niepoprawnie identyfikuje błędy pisowni w wyrazy złożone, takich jak "Hausnummer" w języku niemieckim.</li></ul>|
|Sugestia|Problem #1 — ten problem został rozwiązany w programie .NET Framework 4.6.2 problem nr 2 — Moduł sprawdzania pisowni WPF nie jest już obsługiwana w przypadku aplikacji na rynek za pomocą polecenia "Uruchom jako inny użytkownik". Począwszy od .NET Framework 4.6.2, aplikacje uruchomione w ten sposób nie będzie nieoczekiwaną awarię — zamiast tego sprawdzania pisowni będzie dyskretnie wyłączone. Problem #3 — ten problem został rozwiązany w programie .NET Framework 4.6.2.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|

