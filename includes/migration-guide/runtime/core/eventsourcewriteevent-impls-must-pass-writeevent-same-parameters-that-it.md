### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls należy przekazać WriteEvent tych samych parametrów, które otrzymał (plus identyfikator)

|   |   |
|---|---|
|Szczegóły|Środowisko wykonawcze wymusza teraz kontraktu, który określa następujące elementy: klasą pochodną <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> definiujący ETW metody zdarzeń należy wywołać klasy bazowej <code>EventSource.WriteEvent</code> metody z Identyfikatorem zdarzenia następuje te same argumenty, które zostały metody zdarzeń ETW przekazany.|
|Sugestia|<xref:System.IndexOutOfRangeException?displayProperty=name> Wyjątek jest generowany, jeśli <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytuje <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> danych w procesie dla źródła zdarzenia, który narusza aktualne niniejszej Umowy.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

