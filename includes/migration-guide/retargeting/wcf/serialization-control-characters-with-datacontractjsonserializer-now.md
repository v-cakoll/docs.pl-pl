---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614791"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer jest teraz zgodna z ECMAScript V6 i V8

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> nie serializacji niektórych specjalnych znaków kontroli, takich jak \b, \f i \t, w sposób zgodny z standardami ECMAScript V6 i V8. Począwszy od .NET Framework 4,7, serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla .NET Framework 4,7 ta funkcja jest domyślnie włączona. Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
