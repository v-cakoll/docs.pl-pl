---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981449"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey zwraca RSACng net462 (lub lightup) bez zmiany retargetingu

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, konkretny typ obiektu zwracanego przez <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> zmienić metody (bez niedoskonałość) od implementacji CryptoServiceProvider implementacji Cng. Jest to spowodowane implementacji zmieniła się z pomocą <code>certificate.PublicKey.Key</code> za pomocą wewnętrznego <code>certificate.GetAnyPublicKey</code> który przekazuje do <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Sugestia|Począwszy od aplikacji działających w środowisku .NET Framework 4.7.1, możesz użyć implementacji CryptoServiceProvider, używany domyślnie w programie .NET Framework 4.6.1 i wcześniejszych wersjach, dodając następującą konfigurację przejdź do [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji w pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
