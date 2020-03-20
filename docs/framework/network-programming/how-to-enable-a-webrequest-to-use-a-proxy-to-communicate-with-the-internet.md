---
title: 'Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039536"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest

W tym przykładzie tworzy wystąpienie <xref:System.Net.WebRequest> globalnego serwera proxy, które umożliwi każdemu używanie serwera proxy do komunikowania się z Internetem. W przykładzie przyjęto założenie, `webproxy` że serwer proxy ma nazwę i że komunikuje się na porcie 80, standardowym porcie HTTP.

## <a name="example"></a>Przykład

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- [ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) C# dla **System.Net** przestrzeni nazw.
- Instrukcja Języka Visual [ `Imports` Basic](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla **System.Net** obszaru nazw.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
