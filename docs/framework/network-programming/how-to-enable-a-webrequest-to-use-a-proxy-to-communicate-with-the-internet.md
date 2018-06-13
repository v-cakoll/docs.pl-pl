---
title: 'Porady: Włączanie WebRequest do korzystania z serwera Proxy do komunikacji z Internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0f57869dfecce3e59d0a255a6201dd966bc407e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396909"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="10f78-102">Porady: Włączanie WebRequest do korzystania z serwera Proxy do komunikacji z Internetem</span><span class="sxs-lookup"><span data-stu-id="10f78-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="10f78-103">W tym przykładzie tworzy wystąpienie globalnych serwera proxy, które umożliwi żadnego <xref:System.Net.WebRequest> do korzystania z serwera proxy do komunikacji z Internetem.</span><span class="sxs-lookup"><span data-stu-id="10f78-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="10f78-104">W przykładzie założono, że serwer proxy ma nazwę `webproxy` i że komunikujących się z portu 80, standardowego portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="10f78-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f78-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="10f78-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10f78-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="10f78-106">Compiling the Code</span></span>  
 <span data-ttu-id="10f78-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="10f78-107">This example requires:</span></span>  
  
-   <span data-ttu-id="10f78-108">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="10f78-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f78-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10f78-109">See Also</span></span>  
 [<span data-ttu-id="10f78-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="10f78-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="10f78-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="10f78-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
