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
ms.workload: dotnet
ms.openlocfilehash: 68871505e735485dd73d219b4144d56eabe21e43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="098e7-102">Porady: Włączanie WebRequest do korzystania z serwera Proxy do komunikacji z Internetem</span><span class="sxs-lookup"><span data-stu-id="098e7-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="098e7-103">W tym przykładzie tworzy wystąpienie globalnych serwera proxy, które umożliwi żadnego <xref:System.Net.WebRequest> do korzystania z serwera proxy do komunikacji z Internetem.</span><span class="sxs-lookup"><span data-stu-id="098e7-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="098e7-104">W przykładzie założono, że serwer proxy ma nazwę `webproxy` i że komunikujących się z portu 80, standardowego portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="098e7-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="098e7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="098e7-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="098e7-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="098e7-106">Compiling the Code</span></span>  
 <span data-ttu-id="098e7-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="098e7-107">This example requires:</span></span>  
  
-   <span data-ttu-id="098e7-108">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="098e7-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098e7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="098e7-109">See Also</span></span>  
 [<span data-ttu-id="098e7-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="098e7-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="098e7-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="098e7-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
