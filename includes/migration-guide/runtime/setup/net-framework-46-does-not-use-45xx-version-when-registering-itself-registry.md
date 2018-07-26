### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 nie korzystają z wersji 4.5.x.x po zarejestrowaniu się w rejestrze

|   |   |
|---|---|
|Szczegóły|Jak można oczekiwać, że, klucz wersji ustawiony w rejestrze (w <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) dla programu .NET Framework 4.6 zaczyna się od "4.6", nie 4.5. Aplikacje, które są zależne od tych kluczy rejestru, aby dowiedzieć się, które wersje .NET Framework są zainstalowane na maszynie powinien zostać zaktualizowany, aby zrozumieć, 4.6 jest nowa wersja możliwe i taki, który jest zgodny z 4.5.x poprzednie wersje.|
|Sugestia|Aktualizuj aplikacje sondowania dla .NET Framework 4.5 Zainstaluj, wyszukując 4.5 klucze rejestru, aby także zaakceptować 4.6.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

