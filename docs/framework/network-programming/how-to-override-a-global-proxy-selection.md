---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
description: Postępuj zgodnie z tym przykładem, aby zastąpić globalne Wybieranie serwera proxy przez wysłanie żądania webżądanie do adresu URL, które zastępuje wybór z serwerem proxy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502512"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Instrukcje: zastępowanie wyboru globalnego serwera proxy
W tym przykładzie wysłano **żądanie** sieci webdo `www.contoso.com` , które zastąpi globalny wybór serwera proxy serwerem proxy o nazwie `alternateproxy` na porcie 80.  
  
## <a name="example"></a>Przykład  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- [ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) dla przestrzeni nazw **System.NET** .  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](accessing-the-internet-through-a-proxy.md)
