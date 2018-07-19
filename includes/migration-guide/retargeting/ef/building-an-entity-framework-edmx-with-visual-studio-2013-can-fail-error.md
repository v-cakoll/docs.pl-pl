### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Tworzenie edmx Entity Framework w programie Visual Studio 2013 może zakończyć się niepowodzeniem z powodu błędu MSB4062 korzystania z zadań EntityDeploySplit lub EntityClean

|   |   |
|---|---|
|Szczegóły|Narzędzia MSBuild 12.0 (dołączone do programu Visual Studio 2013) zmienić lokalizacje plików programu MSBuild, powodując starsze pliki obiektów docelowych programu Entity Framework jest nieprawidłowy. W wyniku <code>EntityDeploySplit</code> i <code>EntityClean</code> zadań zakończy się niepowodzeniem, ponieważ nie można odnaleźć <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Należy pamiętać, że ten podział ze względu na zmiany zestawu narzędzi (MSBuild/VS) nie ze względu na zmiany w .NET Framework. Tylko wystąpi podczas uaktualniania narzędzia dla deweloperów, nie wtedy, gdy tylko uaktualniania programu .NET Framework.|
|Sugestia|Entity Framework cele pliki są stałe do pracy z nowego rozpoczynający układ MSBuild w .NET Framework 4.6. Uaktualnienie do tej wersji w ramach rozwiąże ten problem. Alternatywnie [to](http://stackoverflow.com/a/24249247/131944) obejście może służyć do poprawiania bezpośrednio pliki obiektów docelowych.|
|Zakres|Główne|
|Wersja|4.5.1|
|Typ|Trwa przekierowywanie|

