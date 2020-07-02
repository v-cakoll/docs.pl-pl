---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616095"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml. GetPublicKey zwraca RSACng na net462 (lub lightup) bez przekierowania zmiany

#### <a name="details"></a>Szczegóły

Rozpoczynając od .NET Framework 4.6.2, konkretny typ obiektu zwróconego przez <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodę został zmieniony (bez Quirk) z implementacji CryptoServiceProvider do implementacji CNG. Wynika to z faktu, że implementacja zmieniła się z użycia `certificate.PublicKey.Key` na do użycia wewnętrznego, `certificate.GetAnyPublicKey` do którego przekazuje <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .

#### <a name="suggestion"></a>Sugestia

Począwszy od aplikacji uruchomionych na .NET Framework 4.7.1 można użyć implementacji CryptoServiceProvider używanej domyślnie w .NET Framework 4.6.1 i starszych wersjach, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
