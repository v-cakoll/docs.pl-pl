### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zakleszczenie może powodować podczas korzystania z usługi współużytkowane

|   |   |
|---|---|
|Szczegóły|Zakleszczenie może skutkować współużytkowane usługi, który ogranicza wystąpień usługi jeden wątek na raz. Usługi podatne na ten problem będzie występował będzie mieć następujące <xref:System.ServiceModel.ServiceBehaviorAttribute> w ich kodu:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Sugestia|Aby rozwiązać ten problem, można wykonać następujące czynności:<ul><li>Ustaw tryb współbieżności usługi <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> lub &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Na przykład:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Zainstaluj najnowszą aktualizację programu .NET Framework 4.6.2, lub Uaktualnij do nowszej wersji programu .NET Framework. Powoduje wyłączenie przepływ <xref:System.Threading.ExecutionContext> w <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. To zachowanie jest konfigurowalne; odpowiada to dodanie następującego ustawienia app do pliku konfiguracji:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Wartość <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> nigdy nie powinien być ustawiony na <code>false</code> Rentrant usług.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

