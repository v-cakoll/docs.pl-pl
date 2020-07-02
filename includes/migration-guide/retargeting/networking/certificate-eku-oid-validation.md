---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615683"
---
### <a name="certificate-eku-oid-validation"></a>Walidacja identyfikatora OID certyfikatu EKU

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6, <xref:System.Net.Security.SslStream> klasy lub <xref:System.Net.ServicePointManager> służą do wykonywania walidacji identyfikatora obiektu (EKU) ulepszonego użycia klucza. Rozszerzenie ulepszonego użycia klucza (EKU) to zbiór identyfikatorów obiektów (OID) wskazujący aplikacje, które używają klucza. Walidacja identyfikatora OID rozszerzenia EKU używa zdalnego wywołania zwrotnego certyfikatu w celu upewnienia się, że certyfikat zdalny ma poprawne identyfikatory OID dla zamierzonego celu.

#### <a name="suggestion"></a>Sugestia

Jeśli ta zmiana jest niepożądana, można wyłączyć weryfikację identyfikatorów OID certyfikatu, dodając następujący przełącznik do [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> To ustawienie jest dostępne wyłącznie w celu zapewnienia zgodności z poprzednimi wersjami. Jego użycie nie jest zalecane.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
