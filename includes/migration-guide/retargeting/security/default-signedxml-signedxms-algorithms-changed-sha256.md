---
ms.openlocfilehash: 12ba683655319e42368f9f2a6cf7bf70e1dbd77d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859026"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Algorytmy SignedXML domyślne i SignedXMS zmieniony na SHA256

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7 i starszych SignedXML i SignedCMS domyślne SHA1 dla niektórych operacji. Począwszy od programu .NET Framework 4.7.1 SHA256 jest domyślnie włączona dla tych operacji. Ta zmiana jest konieczne, ponieważ SHA1 przestaje być uważany za zabezpieczony.|
|Sugestia|Czy domyślnie używany jest algorytm SHA1 (niebezpieczne) lub SHA256 są dwa nowe wartości przełącznika kontekstu do kontroli:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>W przypadku aplikacji, dla środowiska .NET Framework 4.7.1 i nowsze wersje, jeśli użycie SHA256 jest niepożądany, można przywrócić domyślną SHA1, dodając następującą konfigurację Przełącz się do [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części pliku config aplikacji Plik:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7 i wcześniejszymi wersjami, możesz zdecydować się na tę zmianę, dodając następujący przełącznik konfiguracji do [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

