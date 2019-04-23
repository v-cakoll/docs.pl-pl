---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127377"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Instrukcje: zastępowanie wyboru globalnego serwera proxy
W tym przykładzie wysyła **WebRequest** do `www.contoso.com` , zastępuje wyboru globalnego serwera proxy przy użyciu serwera proxy, o nazwie `alternateproxy` na porcie 80.  
  
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
  
-   A [ `using` dyrektywy](~/docs/csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
- [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
