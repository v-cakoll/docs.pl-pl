### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Udostępnianie stanu sesji Asp.Net StateServer wymaga wszystkie serwery w farmie sieci web, aby używać tej samej wersji .NET Framework

|   |   |
|---|---|
|Szczegóły|Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stanu sesji, wszystkie serwery w farmie sieci web danego należy używać tej samej wersji programu .NET Framework w kolejności stanu do udostępnienia poprawnie.|
|Sugestia|Pamiętaj uaktualnić wersje programu .NET Framework na serwery sieci web, które współużytkują stanu w tym samym czasie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

