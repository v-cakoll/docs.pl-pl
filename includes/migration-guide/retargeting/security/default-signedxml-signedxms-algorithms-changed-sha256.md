---
ms.openlocfilehash: db076d6799e4de5b8610cf9c1aac79b5386a7229
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859026"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Domyślne algorytmy SignedXML i SignedXMS zostały zmienione na SHA256

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7 i wcześniejszych signedxml i signedcms domyślnie SHA1 dla niektórych operacji. Począwszy od programu .NET Framework 4.7.1, sha256 jest domyślnie włączona dla tych operacji. Ta zmiana jest konieczna, ponieważ SHA1 nie jest już uważane za bezpieczne.|
|Sugestia|Istnieją dwie nowe wartości przełącznika kontekstu do kontrolowania, czy SHA1 (niezabezpieczone) lub SHA256 jest używany domyślnie:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 i nowszych wersji, jeśli użycie sha256 jest niepożądane, można przywrócić wartość domyślną sha1, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.7 i wcześniejszych wersji można zdecydować się na tę zmianę, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|
