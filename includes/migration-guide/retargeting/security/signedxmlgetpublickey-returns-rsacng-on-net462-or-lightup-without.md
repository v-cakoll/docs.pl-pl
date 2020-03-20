---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858920"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey zwraca RSACng w net462 (lub lightup) bez zmiany retargeting

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6.2, konkretny typ <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> obiektu zwrócony przez metodę zmieniono (bez dziwactwa) z CryptoServiceProvider implementacji do implementacji Cng. Dzieje się tak, ponieważ <code>certificate.PublicKey.Key</code> implementacja <code>certificate.GetAnyPublicKey</code> zmieniła się <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>z używania do przy użyciu wewnętrznego, który przekazuje do .|
|Sugestia|Począwszy od aplikacji uruchomionych w programie .NET Framework 4.7.1, można użyć implementacji CryptoServiceProvider używanej domyślnie w programie .NET Framework 4.6.1 i wcześniejszych wersjach, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
