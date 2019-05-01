---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640097"
---
### <a name="certificate-eku-oid-validation"></a>Sprawdzanie poprawności OID rozszerzonego użycia klucza certyfikatu

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6, <xref:System.Net.Security.SslStream> lub <xref:System.Net.ServicePointManager> klas wykonywania weryfikacji identyfikatora (OID) obiektu rozszerzonego użycia klucza (EKU). Rozszerzenie rozszerzone użycie klucza (EKU) to zbiór identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza. Identyfikator OID rozszerzonego użycia klucza weryfikacji używa wywołań zwrotnych certyfikatu zdalnego, aby upewnić się, że certyfikat zdalny prawidłowe identyfikatory OID przeznaczeniem.|
|Sugestia|Jeśli ta zmiana jest niepożądany, możesz wyłączyć certyfikat weryfikacji OID rozszerzonego użycia klucza, dodając następujące przełączyć się do [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) z usługi plik konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne tylko w przypadku zgodności z poprzednimi wersjami. W przeciwnym razie jego użycie nie jest zalecane.</blockquote> |
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
