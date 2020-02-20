---
title: Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452633"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer

Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony tak, aby był zgodny z ECMAScript V6 i V8. 
 
## <a name="impact"></a>Wpływ

W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektórych specjalnych znaków sterujących, takich jak `\b`, `\f`i `\t`, w sposób zgodny z standardami ECMAScript V6 i V8.

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 Serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8. Dotyczy to następujących interfejsów API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Środki zaradcze

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.

Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do sekcji `<runtime>` pliku App. config lub Web. config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
