---
title: 'Instrukcje: Włączanie żądania sieci webdo komunikacji z Internetem za pomocą serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039536"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Instrukcje: Włączanie żądania sieci webdo komunikacji z Internetem za pomocą serwera proxy

W tym przykładzie jest tworzone globalne wystąpienie serwera proxy, które umożliwi <xref:System.Net.WebRequest> do komunikacji z Internetem przy użyciu serwera proxy. W przykładzie przyjęto założenie, że serwer proxy ma nazwę `webproxy` i że komunikuje się z portem 80, standardowym portem HTTP.

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

- C# [Dyrektywa`using`](../../csharp/language-reference/keywords/using-directive.md) dla przestrzeni nazw **System.NET** .
- Visual Basic [`Imports` instrukcji](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla przestrzeni nazw **System.NET** .

## <a name="see-also"></a>Zobacz także

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
