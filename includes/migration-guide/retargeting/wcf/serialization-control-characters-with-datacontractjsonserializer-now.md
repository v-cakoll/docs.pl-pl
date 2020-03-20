---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466062"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializacja znaków sterujących za pomocą datacontractJsonSerializer jest teraz zgodna z ecmascript V6 i V8

|   |   |
|---|---|
|Szczegóły|W programach .NET Framework 4.6.2 i wcześniejszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> nie serializowały niektórych znaków sterujących specjalnych, takich jak \b, \f i \t, w sposób zgodny ze standardami ECMAScript V6 i V8. Począwszy od programu .NET Framework 4.7, serializacja tych znaków sterujących jest zgodna z ecmascript V6 i V8.|
|Sugestia|W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.7 ta funkcja jest domyślnie włączona. Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej <code>&lt;runtime&gt;</code> funkcji, dodając następujący wiersz do sekcji pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
