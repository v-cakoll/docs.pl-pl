### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Powiązania WCF przy użyciu trybu zabezpieczeń TransportWithMessageCredential

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.1 wiązania WCF, który używa trybu zabezpieczeń TransportWithMessageCredential można skonfigurować do odbierania komunikatów za pomocą niepodpisane &quot;do&quot; nagłówki dla kluczy asymetrycznych zabezpieczeń. Domyślnie, niepodpisane &quot;do&quot; nagłówki będą w dalszym ciągu być odrzucone w programie .NET Framework 4.6.1. One tylko będą akceptowane, jeśli ten nowy tryb operacji za pomocą przełącznika konfiguracji Switch.System.ServiceModel.AllowUnsignedToHeader wybranych aplikacji.|
|Sugestia|Ponieważ jest to funkcja opcjonalna, nie powinien wpływać na działanie istniejących aplikacji.<br/>Aby kontrolować, czy nowe zachowanie jest używany, należy użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

