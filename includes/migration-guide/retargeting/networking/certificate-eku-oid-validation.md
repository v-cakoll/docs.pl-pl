---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804481"
---
### <a name="certificate-eku-oid-validation"></a>Sprawdzanie poprawności certyfikatu EKU OID

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework <xref:System.Net.Security.SslStream> 4.6, lub <xref:System.Net.ServicePointManager> klasy wykonać rozszerzone użycie klucza (EKU) identyfikator obiektu (OID) sprawdzania poprawności. Rozszerzenie rozszerzonego użycia klucza (EKU) jest kolekcją identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza. Sprawdzanie poprawności EKU OID używa zdalnych wywołań zwrotnych certyfikatów, aby upewnić się, że certyfikat zdalny ma poprawne identyfikatory OID zgodnie z przeznaczeniem.|
|Sugestia|Jeśli ta zmiana jest niepożądana, można wyłączyć sprawdzanie poprawności OID certyfikatu EKU, dodając następujący przełącznik do [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) [ \<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne tylko w przypadku zgodności z przeszywnie. Jego stosowanie nie jest zalecane.</blockquote> |
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
