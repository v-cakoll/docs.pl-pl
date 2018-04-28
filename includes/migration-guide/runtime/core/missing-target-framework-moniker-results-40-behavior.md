### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Brak wyników Moniker platformy docelowej w zachowaniu 4.0

|   |   |
|---|---|
|Szczegóły|Aplikacje bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> zastosowane w będzie poziomu zestawu automatycznego uruchamiania, używając semantyki (Osobliwości) programu .NET Framework 4.0. W celu zapewnienia wysokiej jakości, zalecane jest, że wszystkie pliki binarne jawnie opatrzone <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> wskazujący wersję platformy .NET zostały skompilowane. Należy zauważyć, że użycie moniker platformy docelowej w pliku projektu spowoduje MSBuild automatycznie zastosować <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Sugestia|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> powinien zostać podany, poprzez dodanie atrybutu bezpośrednio do zestawu lub określając platformy docelowej w [pliku projektu lub za pomocą programu Visual Studio projektu graficznego interfejsu użytkownika właściwości](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

