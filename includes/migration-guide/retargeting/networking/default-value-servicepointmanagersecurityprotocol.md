---
ms.openlocfilehash: 122a5ab3e2def7c19d3d523881fcb15df4dbca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235583"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Domyślną wartością programu ServicePointManager.SecurityProtocol jest SecurityProtocolType.System.Default

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji docelowych .NET Framework 4.7, domyślną wartością <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> właściwości jest <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Ta zmiana umożliwia interfejsom API sieci .NET Framework opartym na strumieniu SslStream (takim jak FTP, HTTPS i SMTP) dziedziczenie domyślnych protokołów zabezpieczeń z systemu operacyjnego zamiast wartości zakodowanych na podstawie wartości zakodowanych zdefiniowanych przez program .NET Framework. Wartość domyślna zależy od systemu operacyjnego i dowolnej konfiguracji niestandardowej wykonywanej przez administratora systemu. Aby uzyskać informacje na temat domyślnego protokołu SChannel w każdej wersji systemu operacyjnego Windows, zobacz [Protokoły w protokołach TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>W przypadku aplikacji przeznaczonych dla starszej wersji programu <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> .NET Framework wartość domyślna właściwości zależy od wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [sekcję Sieć retargetingu zmiany migracji z programu .NET Framework 4.5.2 do 4.6.](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)|
|Sugestia|Ta zmiana dotyczy aplikacji docelowych w wersji .NET Framework 4.7 lub nowszej. <br>Jeśli wolisz używać zdefiniowanego protokołu, a nie polegać na domyślnym systemie, możesz jawnie ustawić wartość <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> właściwości.<br>Jeśli ta zmiana jest niepożądana, można zrezygnować z niej, dodając ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji. Poniższy przykład przedstawia <code>&lt;runtime&gt;</code> zarówno <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> sekcję, jak i przełącznik rezygnacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|
