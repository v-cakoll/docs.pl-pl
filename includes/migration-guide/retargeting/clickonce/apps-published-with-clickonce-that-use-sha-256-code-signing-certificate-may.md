### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikacje opublikowane za pomocą technologii ClickOnce, korzystających z algorytmu SHA-256 certyfikat podpisywania kodu może zakończyć się niepowodzeniem w systemie Windows 2003

|   |   |
|---|---|
|Szczegóły|Plik wykonywalny jest podpisany przy użyciu SHA256. Wcześniej został on podpisany SHA1 niezależnie od tego, czy certyfikat podpisywania kodu został SHA-1 lub SHA-256. Dotyczy to:<ul><li>Wszystkie aplikacje utworzone przy użyciu programu Visual Studio 2012 lub nowszym.</li><li>Aplikacji utworzonych za pomocą programu Visual Studio 2010 lub wcześniej w przypadku systemów za pomocą programu .NET Framework 4.5 obecne.</li></ul>Ponadto jeśli .NET Framework 4.5 lub nowszej jest obecny, ClickOnce manifest są także podpisane przy użyciu algorytmu SHA-256 w przypadku certyfikatów SHA-256, niezależnie od wersji programu .NET Framework, względem którego został skompilowany.|
|Sugestia|Zmiana z rejestracją ClickOnce pliku wykonywalnego dotyczy tylko systemów Windows Server 2003; wymagają one, że KB 938397 zostanie zainstalowany. Zmiana podpisywania manifestu za pomocą algorytmu SHA-256, nawet wtedy, gdy aplikacja jest przeznaczony dla .NET Framework 4.0 i jego wcześniejsze wersje wprowadza zależność środowiska uruchomieniowego .NET Framework 4.5 lub nowszej wersji.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|

