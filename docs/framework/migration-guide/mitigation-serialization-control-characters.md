---
title: Serializacja znaków kontrolnych za pomocą datacontractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181209"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Łagodzenie: Serializacja znaków kontrolnych za pomocą datacontractJsonSerializer

Począwszy od programu .NET Framework 4.7, sposób, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> w jaki znaki sterujące są serializowane z został zmieniony, aby były zgodne z ECMAScript V6 i V8.

## <a name="impact"></a>Wpływ

W programach .NET Framework 4.6.2 i wcześniejszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie `\b`serializowały niektórych znaków sterujących specjalnych, takich jak , `\f`i `\t`, w sposób zgodny ze standardami ECMAScript V6 i V8.

W przypadku aplikacji docelowych wersji programu .NET Framework, począwszy od platformy .NET Framework 4.7, serializacja tych znaków sterujących jest zgodna z systemami ECMAScript V6 i V8. Dotyczy to następujących interfejsów API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Środki zaradcze

W przypadku aplikacji docelowych wersji programu .NET Framework, począwszy od programu .NET Framework 4.7, to zachowanie jest domyślnie włączone.

Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej `<runtime>` funkcji, dodając następujący wiersz do sekcji pliku app.config lub web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
