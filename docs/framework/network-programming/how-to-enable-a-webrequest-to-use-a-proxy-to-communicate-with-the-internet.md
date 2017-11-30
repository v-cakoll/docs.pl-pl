---
title: "Porady: Włączanie WebRequest do korzystania z serwera Proxy do komunikacji z Internetem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 937f4ac06ef4788c42b364fe03226e32a55572f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Porady: Włączanie WebRequest do korzystania z serwera Proxy do komunikacji z Internetem
W tym przykładzie tworzy wystąpienie globalnych serwera proxy, które umożliwi żadnego <xref:System.Net.WebRequest> do korzystania z serwera proxy do komunikacji z Internetem. W przykładzie założono, że serwer proxy ma nazwę `webproxy` i że komunikujących się z portu 80, standardowego portu HTTP.  
  
## <a name="example"></a>Przykład  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do **System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Dostęp do Internetu za pośrednictwem serwera Proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
