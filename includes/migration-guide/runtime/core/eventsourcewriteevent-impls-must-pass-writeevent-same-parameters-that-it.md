### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls należy przekazać metody WriteEvent tego samego parametrów, które otrzymał (oraz identyfikator)

|   |   |
|---|---|
|Szczegóły|Środowisko uruchomieniowe teraz wymusza kontraktu, który określa następujące: klasą pochodną <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> definiuje ETW metody zdarzenia musi wywoływać klasę podstawową <code>EventSource.WriteEvent</code> metody o identyfikatorze zdarzenia następuje te same argumenty, które metoda zdarzenia ETW przekazany.|
|Sugestia|<xref:System.IndexOutOfRangeException?displayProperty=name> Jest zgłaszany wyjątek, jeśli <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytuje <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> danych w procesie dla źródła zdarzenia, który narusza tego kontraktu.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|środowisko uruchomieniowe|

