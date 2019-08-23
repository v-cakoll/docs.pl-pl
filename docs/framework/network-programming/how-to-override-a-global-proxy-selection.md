---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: e5f4dc22ad75dc4d4f7dc30f44e6ae304403ef16
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914529"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Instrukcje: zastępowanie wyboru globalnego serwera proxy
W tym przykładzie wysłano **żądanie** sieci `www.contoso.com` webdo, które zastąpi globalny wybór serwera proxy `alternateproxy` serwerem proxy o nazwie na porcie 80.  
  
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
  
- Dyrektywa dla przestrzeni nazw **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
