---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859289"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu CNG

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji docelowych .NET Framework 4.6.2, zabezpieczenia transportu WCF obsługuje certyfikaty przechowywane przy użyciu biblioteki kryptografii systemu Windows (CNG). Ta obsługa jest ograniczona do certyfikatów z kluczem publicznym, który ma wykładnik nie więcej niż 32 bitów długości. Gdy aplikacja jest przeznaczona dla programu .NET Framework 4.6.2, ta funkcja jest domyślnie włączona. We wcześniejszych wersjach programu .NET Framework próba użycia certyfikatów X509 z dostawcą magazynu kluczy CSG zgłasza wyjątek.|
|Sugestia|Aplikacje przeznaczone dla programu .NET Framework 4.6.1 i wcześniejszych, ale uruchomione w programie .NET Framework 4.6.2, mogą włączyć obsługę certyfikatów CNG, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Można to również zrobić programowo za pomocą następującego kodu:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Należy zauważyć, że z powodu tej zmiany wszelkie wyjątki obsługi kodu, który zależy od próby zainicjowania bezpiecznej komunikacji z certyfikatem CNG zakończyć się niepowodzeniem nie będzie już wykonywane.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
