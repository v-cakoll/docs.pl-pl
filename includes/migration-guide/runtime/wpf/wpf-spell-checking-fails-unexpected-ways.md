### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Sprawdzanie pisowni WPF nie powiedzie się w nieoczekiwany sposób.

|   |   |
|---|---|
|Szczegóły|Obejmuje to wiele problemów WPF moduł sprawdzania pisowni:<ul><li>Czasami zgłasza sprawdzania pisowni WPF <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Moduł sprawdzania pisowni WPF kończy się niepowodzeniem z <xref:System.UnauthorizedAccessException> podczas uruchamiania aplikacji za pomocą polecenia "Uruchom jako inny użytkownik"</li><li>Moduł sprawdzania pisowni WPF nieprawidłowo zidentyfikować błędów pisowni w wyrazy złożone, takie jak "Hausnummer" w języku niemieckim.</li></ul>|
|Sugestia|#1 - problem ten został rozwiązany dla programu .NET Framework 4.6.2 problem #2 — Moduł sprawdzania pisowni WPF nie jest już obsługiwana podczas uruchamiania aplikacji za pomocą polecenia "Uruchom jako inny użytkownik". Począwszy od platformy .NET Framework 4.6.2, aplikacje uruchomione w ten sposób już ulegnie awarii nieoczekiwanie — zamiast tego sprawdzania pisowni zostanie dyskretnie wyłączone. #3 - problem ten został rozwiązany dla programu .NET Framework 4.6.2.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|środowisko uruchomieniowe|

