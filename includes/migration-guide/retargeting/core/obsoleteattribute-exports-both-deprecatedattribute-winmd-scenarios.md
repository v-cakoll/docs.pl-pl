### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute eksportuje zarówno jako ObsoleteAttribute i DeprecatedAttribute w scenariuszach WinMD

|   |   |
|---|---|
|Szczegóły|Podczas tworzenia biblioteki metadanych systemu Windows (plik winmd) <xref:System.ObsoleteAttribute?displayProperty=name> atrybutu jest eksportowane jako zarówno <xref:System.ObsoleteAttribute?displayProperty=name> i [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Sugestia|Ponowna kompilacja elementu istniejącego kodu źródłowego, który używa <xref:System.ObsoleteAttribute?displayProperty=name> atrybut może generować ostrzeżenia w przypadku uzyskiwania dostępu do kodu w języku C + +/ CX lub JavaScript.We nie zaleca się stosowania zarówno <xref:System.ObsoleteAttribute?displayProperty=name> i [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kod w zarządzanych zestawów; może to spowodować ostrzeżeń kompilacji.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Przekierowania|

