---
title: 'Porady: Zastąp wybór globalnych serwera Proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c10cff979a18d8e07a1e7089f96157e4c38f040e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393909"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Porady: Zastąp wybór globalnych serwera Proxy
W tym przykładzie wysyła **WebRequest** do www.contoso.com zastępujący wybór globalnych serwera proxy z serwerem proxy o nazwie `alternateproxy` na porcie 80.  
  
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
  
-   Odwołuje się do **System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Dostęp do Internetu za pośrednictwem serwera proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
