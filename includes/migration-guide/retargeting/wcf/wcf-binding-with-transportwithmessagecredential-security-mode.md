---
ms.openlocfilehash: 2359dafb9042c13ae75e644d4ea655f53c14e95e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804323"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Powiązanie WCF z trybem zabezpieczeń TransportWithMessageCredential

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6.1, WCF powiązanie, które używa TransportWithMessageCredential tryb zabezpieczeń &quot;&quot; można skonfigurować do odbierania wiadomości z niepodpisanych do nagłówków dla asymetrycznych kluczy zabezpieczeń. Domyślnie &quot;niepodpisane&quot; do nagłówków będą nadal odrzucane w .NET Framework 4.6.1. Będą one akceptowane tylko wtedy, gdy aplikacja zdecyduje się na ten nowy tryb działania za pomocą switch.system.ServiceModel.AllowUnsignedToHeader przełącznika konfiguracji.|
|Sugestia|Ponieważ jest to funkcja opt-in, nie powinna wpływać na zachowanie istniejących aplikacji.<br/>Aby kontrolować, czy nowe zachowanie jest używane, należy użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
