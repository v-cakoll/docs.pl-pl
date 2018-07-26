### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>EntryPointNotFoundExceptions niektórych interfejsów API platformy .NET Przyczyna pierwszej szansy (obsługiwane)

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5 niewielkiej liczby metod .NET rozpoczął się zgłaszanie pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=name>s. Wyjątki te zostały obsłużone w ramach programu .NET Framework, ale można podzielić Automatyzacja testów, które nie oczekiwano elementu wyjątki pierwszej szansy. Tych tych samych interfejsów API przerwanie Niektóre scenariusze ApiVerifier po włączeniu HighVersionLie.|
|Sugestia|Po uaktualnieniu do programu .NET Framework 4.5.1 można uniknąć tego błędu. Alternatywnie można zaktualizować Automatyzacja testów nie włamanie się na pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

