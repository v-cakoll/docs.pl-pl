### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase już jest wybierane przez userandomizedstringhashalgorithm —

|   |   |
|---|---|
|Szczegóły|Przed .NET Framework 4.6, wartość <xref:System.AppDomainSetup.DynamicBase> może być wybierane między domenami aplikacji lub procesy, jeśli userandomizedstringhashalgorithm — zostało włączone w pliku konfiguracyjnym aplikacji. W programie .NET Framework 4.6 <xref:System.AppDomainSetup.DynamicBase> zwróci wynik stabilna między różnymi wystąpieniami uruchamiania aplikacji i między domenami różnych aplikacji. Dynamiczne podstaw nadal będą się różnić dla różnych aplikacji. Ta zmiana spowoduje usunięcie tylko losowe elementu nazewnictwa dla różnych wystąpień tej samej aplikacji.|
|Sugestia|Należy pamiętać, że włączenie <code>UseRandomizedStringHashAlgorithm</code> nie spowoduje <xref:System.AppDomainSetup.DynamicBase> są wybierane. W razie potrzeby losowe base muszą być produkowane w kodzie aplikacji, a nie za pośrednictwem tego interfejsu API.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

