---
title: 'Instrukcje: Włącz używanie serwera Proxy do komunikacji z Internetem przez element WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d8bcf20831a806694ab40ed7584365d8109e1460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689016"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="0a68b-102">Instrukcje: Włącz używanie serwera Proxy do komunikacji z Internetem przez element WebRequest</span><span class="sxs-lookup"><span data-stu-id="0a68b-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="0a68b-103">Ten przykład tworzy wystąpienie globalnych serwera proxy, które spowoduje włączenie dowolnego <xref:System.Net.WebRequest> korzystania z serwera proxy do komunikacji z Internetem.</span><span class="sxs-lookup"><span data-stu-id="0a68b-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="0a68b-104">W przykładzie założono, że serwer proxy ma nazwę `webproxy` i że komunikuje się ona na port 80, standardowego portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0a68b-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a68b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a68b-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0a68b-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0a68b-106">Compiling the Code</span></span>  
 <span data-ttu-id="0a68b-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0a68b-107">This example requires:</span></span>  
  
-   <span data-ttu-id="0a68b-108">A [ `using` dyrektywy](../../csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0a68b-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a68b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a68b-109">See also</span></span>
- [<span data-ttu-id="0a68b-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="0a68b-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="0a68b-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="0a68b-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
