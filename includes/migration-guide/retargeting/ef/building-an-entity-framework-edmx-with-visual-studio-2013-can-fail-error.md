### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Tworzenie pliku edmx Entity Framework z programu Visual Studio 2013 może zakończyć się niepowodzeniem z powodu błędu MSB4062 Jeśli za pomocą zadań EntityDeploySplit lub EntityClean

|   |   |
|---|---|
|Szczegóły|Narzędzia MSBuild 12.0 (dołączone do programu Visual Studio 2013) zmienić MSBuild lokalizacje plików, co powoduje starsze pliki cele Entity Framework jest nieprawidłowy. W wyniku <code>EntityDeploySplit</code> i <code>EntityClean</code> zadań zakończy się niepowodzeniem, ponieważ nie można odnaleźć <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Należy pamiętać, że ten podział ze względu na zmiany (MSBuild/VS) zestawu narzędzi nie ze względu na zmiany .NET Framework. Tylko wystąpią, gdy uaktualniania narzędzi dla deweloperów, nie w przypadku, gdy tylko uaktualniania programu .NET Framework.|
|Sugestia|Usunięto Entity Framework cele plików do pracy z nowego MSBuild układu począwszy od wersji programu .NET Framework 4.6. Uaktualnianie do tej wersji platformy naprawi ten problem. Alternatywnie [to](http://stackoverflow.com/a/24249247/131944) obejście może służyć do bezpośrednio poprawka plików obiektów docelowych.|
|Zakres|Główne|
|Wersja|4.5.1|
|Typ|Przekierowania|

