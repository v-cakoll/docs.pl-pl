---
title: Środki zaradcze Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789847"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Środki zaradcze Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer

Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony, aby był zgodny z ECMAScript V6 i V8. 
 
## <a name="impact"></a>Wpływ

W programie .NET Framework <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 4.6.2 i starszych wersjach nie serializacji niektórych specjalnych znaków kontroli, takich jak `\b`, `\f`, i `\t`w sposób zgodny z standardami ECMAScript V6 i V8.

W przypadku aplikacji przeznaczonych dla wersji .NET Framework rozpoczynających się od .NET Framework 4,7, serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8. Dotyczy to następujących interfejsów API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Ograniczenie

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.

Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku App. config lub Web. config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Zobacz także

- [Przekierowywanie zmian w .NET Framework 4,7](retargeting-changes-in-the-net-framework-4-7.md)
