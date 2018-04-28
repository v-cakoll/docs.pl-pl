### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase — nie propagację wyjątki OnStart

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7 i wcześniejszych wersjach, wyjątków zgłaszanych na uruchomienia usługi nie są propagowane do wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>. Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 środowiska uruchomieniowego propaguje wyjątki <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> dla usług, które się nie uruchomić.|
|Sugestia|Po uruchomieniu usługi Jeśli występuje wyjątek, ten wyjątek będzie propagowane. Powinno to zdiagnozowania przypadków, w którym usługi się nie uruchomić. Jeśli to zachowanie jest niepożądane, można zrezygnować z go, dodając następujące <AppContextSwitchOverrides> elementu <runtime> sekcji pliku konfiguracji aplikacji:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli aplikacja jest przeznaczony dla starszej wersji niż 4.7.1, ale mają ten problem, Dodaj następujący <AppContextSwitchOverrides> elementu <runtime> sekcji pliku konfiguracji aplikacji:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

