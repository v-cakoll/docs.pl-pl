### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>Zestawy skompilowane z podziału Regex.CompileToAssembly 4.0 i 4.5

|   |   |
|---|---|
|Szczegóły|Jeśli zestaw skompilowane wyrażenia regularnego jest zbudowany z programu .NET Framework 4.5, ale obiektów docelowych programu .NET Framework 4, próba użycia jednego z wyrażeń regularnych, w tym zestaw w systemie .NET Framework 4 zainstalowany zgłasza wyjątek.|
|Sugestia|Aby obejść ten problem, wykonaj następujące czynności:<ul><li>Utwórz zestaw, który zawiera wyrażenia regularne z programu .NET Framework 4.</li><li>Użycie wyrażenia regularnego interpretowany.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

