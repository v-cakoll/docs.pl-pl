### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>EntryPointNotFoundExceptions niektórych interfejsów API architektury .NET Przyczyna pierwszej szansy (obsługiwane)

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 niewielką liczbę metod .NET rozpoczął się wyrzucanie pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=name>s. Wyjątki te zostały obsłużone w programie .NET Framework, ale może spowodować przerwanie automatyzacji testów, które nie oczekiwano wyjątki pierwszej szansy. Te tych samych interfejsów API Przerwij ApiVerifier sytuacje, w przypadku HighVersionLie jest włączona.|
|Sugestia|Tego błędu można uniknąć przez uaktualnienie do systemu .NET Framework 4.5.1. Alternatywnie można aktualizować automatyzacji testu nie włamanie się na pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

