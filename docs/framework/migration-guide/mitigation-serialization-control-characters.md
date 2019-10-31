---
title: 'Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 5f8218d0f369f25b1add501fdc975d6dccfe90fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126150"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer

Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony tak, aby był zgodny z ECMAScript V6 i V8. 
 
## <a name="impact"></a>Wpływ

W programie .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektórych specjalnych znaków sterujących, takich jak `\b`, `\f`i `\t`, w sposób zgodny z standardami ECMAScript V6 i V8.

W przypadku aplikacji przeznaczonych dla wersji .NET Framework rozpoczynających się od .NET Framework 4,7, serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8. Dotyczy to następujących interfejsów API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Ograniczenie

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.

Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do sekcji `<runtime>` pliku App. config lub Web. config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Zobacz także

- [Przekierowywanie zmian w .NET Framework 4,7](retargeting-changes-in-the-net-framework-4-7.md)
