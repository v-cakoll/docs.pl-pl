### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Przepływ pracy zgłasza teraz pierwotny wyjątek zamiast NullReferenceException w niektórych przypadkach

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.6.2 i starszych wersjach, gdy metody Execute działania przepływu pracy zgłasza wyjątek z <code>null</code> wartość <xref:System.Exception.Message> zgłasza środowiska uruchomieniowego przepływu pracy elementu System.Activities właściwość <xref:System.NullReferenceException?displayProperty=name>, maskowania pierwotny wyjątek. W 4.7 Framework .NET wcześniej maskowanego wyjątku.|
|Sugestia|Jeśli obsługa zależy od kodu <xref:System.NullReferenceException?displayProperty=name>, Zmień, aby przechwytywać wyjątki, które może zostać zgłoszony z własnych działań.|
|Zakres|Pomocnicza|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

