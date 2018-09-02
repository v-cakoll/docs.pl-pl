### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Brak Moniker platformy docelowej powoduje zachowanie 4.0

|   |   |
|---|---|
|Szczegóły|Aplikacje bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> zastosowano zestaw będzie poziomu automatycznego uruchamiania, za pomocą semantyki (Osobliwości) .NET Framework 4.0. W celu zapewnienia wysokiej jakości, zalecane jest, że wszystkie pliki binarne można jawnie przypisać z <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> wskazujący wersję programu .NET Framework zostały skompilowane. Należy pamiętać, że korzystanie z monikerem platformy docelowej w pliku projektu spowoduje, że program MSBuild, aby automatycznie zastosować <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Sugestia|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> powinien być dostarczony, poprzez dodanie atrybutu bezpośrednio do zestawu lub określanie platformy docelowej, w [pliku projektu lub za pomocą programu Visual Studio projektu graficznego interfejsu użytkownika właściwości](https://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

