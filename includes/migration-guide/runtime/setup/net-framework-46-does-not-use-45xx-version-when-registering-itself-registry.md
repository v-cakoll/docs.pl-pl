### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 nie korzystają z wersji 4.5.x.x po zarejestrowaniu się w rejestrze

|   |   |
|---|---|
|Szczegóły|Zgodnie z jedną może spodziewać się klucz wersji ustawiony w rejestrze (w <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) dla programu .NET Framework 4.6 rozpoczyna się od "4.6", nie 4.5. Aplikacje, które są zależne od te klucze rejestru, aby dowiedzieć się, które wersje .NET Framework są zainstalowane na maszynie powinny zostać uaktualnione do zrozumienia 4.6 jest nowa wersja to możliwe, czy jest niezgodny z poprzednim 4.5.x zwalnia.|
|Sugestia|Zainstaluj aplikacje aktualizacji sondowanie dla platformy .NET Framework 4.5, wyszukując 4.5 klucze rejestru, aby zaakceptować również 4.6.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|środowisko uruchomieniowe|

