### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikacje opublikowane za pomocą technologii ClickOnce, korzystających z algorytmu SHA-256 certyfikat podpisywania kodu może zakończyć się niepowodzeniem w systemie Windows 2003

|   |   |
|---|---|
|Szczegóły|Plik wykonywalny jest podpisany za pomocą SHA256. Wcześniej był podpisany z SHA1 niezależnie od tego, czy certyfikat podpisywania kodu został SHA-1 lub SHA-256. Dotyczy to:<ul><li>Wszystkie aplikacje skompilowane z programu Visual Studio 2012 lub nowszym.</li><li>Aplikacje opracowane za pomocą programu Visual Studio 2010 lub wcześniej w przypadku systemów z obecne środowisko .NET Framework 4.5.</li></ul>Ponadto jeśli .NET Framework 4.5 lub nowszej, manifestu aplikacji ClickOnce są także podpisane z algorytmu SHA-256 w przypadku certyfikatów algorytmu SHA-256, niezależnie od wersji programu .NET Framework, względem którego został skompilowany.|
|Sugestia|W pliku wykonywalnego ClickOnce podpisywania dotyczy tylko systemów Windows Server 2003; wymagają zainstalowania KB 938397. Zmiana podpisywanie manifestu z algorytmu SHA-256, nawet wtedy, gdy aplikacja jest przeznaczony dla programu .NET Framework 4.0 i jego wcześniejsze wersje wprowadza zależności środowiska uruchomieniowego .NET Framework 4.5 lub nowszej wersji.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowania|

