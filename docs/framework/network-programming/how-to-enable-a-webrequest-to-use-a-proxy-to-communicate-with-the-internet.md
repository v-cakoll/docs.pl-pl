---
title: 'Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest'
description: Dowiedz się, jak utworzyć globalne wystąpienie serwera proxy, aby umożliwić każdemu elementowi WebRequest korzystanie z serwera proxy w celu komunikowania się z Internetem w .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502538"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest

Ten przykład tworzy globalne wystąpienie serwera proxy, które umożliwi <xref:System.Net.WebRequest> Korzystanie z serwera proxy do komunikowania się z Internetem. W przykładzie przyjęto założenie, że serwer proxy ma nazwę `webproxy` i komunikuje się z portem 80, standardowy port HTTP.

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

- [ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) języka C# dla przestrzeni nazw **System.NET** .
- [ `Imports` Instrukcja](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic dla przestrzeni nazw **System.NET** .

## <a name="see-also"></a>Zobacz także

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
