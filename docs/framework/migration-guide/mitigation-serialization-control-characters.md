---
title: 'Środki zaradcze: Serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182127"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Środki zaradcze: Serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer

Począwszy od .NET Framework 4.7, w sposób, w które określają znaki są było serializować ją przy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony na odpowiadają wersji ECMAScript 6 i V8. 
 
## <a name="impact"></a>Wpływ

W .NET framework 4.6.2 i wcześniejszymi wersjami <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektóre znaki specjalne kontrolki, takie jak `\b`, `\f`, i `\t`, w sposób, który był zgodny ze standardami w wersji ECMAScript 6 i V8.

W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.7 serializacji te znaki kontrolne jest zgodny z wersji ECMAScript 6 i V8. Uwzględnione są następujące funkcje interfejsu API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Ograniczenie

W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.7 to zachowanie jest domyślnie włączona.

Jeśli to zachowanie nie jest pożądane, można zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config lub web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu w programie .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
