---
title: Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
description: Dowiedz się więcej o sposobie zmiany serializacji znaków sterujących w celu zapewnienia zgodności z ECMAScript V6 i V8 w .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475388"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer

Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony na zgodny z ECMAScript V6 i V8.

## <a name="impact"></a>Wpływ

W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializacji niektórych specjalnych znaków kontroli, takich jak `\b` , `\f` i `\t` , w sposób zgodny z standardami ECMAScript V6 i V8.

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 Serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8. Dotyczy to następujących interfejsów API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Ograniczanie ryzyka

W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.

Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
