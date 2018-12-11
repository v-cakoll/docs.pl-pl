### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute eksportuje zarówno jako ObsoleteAttribute i DeprecatedAttribute w scenariuszach WinMD

|   |   |
|---|---|
|Szczegóły|Podczas tworzenia biblioteki metadanych Windows (plik winmd), <xref:System.ObsoleteAttribute?displayProperty=name> atrybutu są eksportowane jako <xref:System.ObsoleteAttribute?displayProperty=name> i [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Sugestia|Ponowna kompilacja elementu istniejący kod źródłowy, który używa <xref:System.ObsoleteAttribute?displayProperty=name> atrybut może generować ostrzeżenia podczas korzystania z tego kodu w języku C + +/ CX lub JavaScript.We nie zaleca się stosowanie zarówno <xref:System.ObsoleteAttribute?displayProperty=name> i [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kodem w zarządzanych zestawów; może to spowodować ostrzeżenia kompilacji.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Przekierowanie|

