### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Wiązania WCF za pomocą trybu zabezpieczeń TransportWithMessageCredential

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.1, powiązania WCF, która używa trybu zabezpieczeń TransportWithMessageCredential można skonfigurować do odbierania wiadomości z niepodpisanych &quot;do&quot; nagłówki dla kluczy asymetrycznych zabezpieczeń. Domyślnie niepodpisane &quot;do&quot; nagłówków będą w dalszym ciągu odrzucone w .NET 4.6.1. One tylko będą akceptowane, jeśli ten nowy tryb działania za pomocą przełącznika konfiguracji Switch.System.ServiceModel.AllowUnsignedToHeader wybranych aplikacji. Ponieważ jest to funkcji opcjonalnych, nie powinna wpływać na działanie istniejących aplikacji.|
|Sugestia|Ponieważ jest to funkcji opcjonalnych, nie powinna wpływać na działanie istniejących aplikacji. Aby kontrolować, czy nowe zachowanie jest używany, należy użyć następującego ustawienia konfiguracji:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.6.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

