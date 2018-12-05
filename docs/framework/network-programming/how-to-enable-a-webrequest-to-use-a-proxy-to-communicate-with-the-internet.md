---
title: 'Porady: Włączanie korzystania z serwera Proxy do komunikacji z Internetem przez element WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 1b10d895478a88556cf1d716480de568c8e9c9ad
ms.sourcegitcommit: 2151690e10d91545e2c20d6b5ad222c162b6b83d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2018
ms.locfileid: "50190446"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="82c99-102">Porady: Włączanie korzystania z serwera Proxy do komunikacji z Internetem przez element WebRequest</span><span class="sxs-lookup"><span data-stu-id="82c99-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="82c99-103">Ten przykład tworzy wystąpienie globalnych serwera proxy, które spowoduje włączenie dowolnego <xref:System.Net.WebRequest> korzystania z serwera proxy do komunikacji z Internetem.</span><span class="sxs-lookup"><span data-stu-id="82c99-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="82c99-104">W przykładzie założono, że serwer proxy ma nazwę `webproxy` i że komunikuje się ona na port 80, standardowego portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="82c99-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c99-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="82c99-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82c99-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="82c99-106">Compiling the Code</span></span>  
 <span data-ttu-id="82c99-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="82c99-107">This example requires:</span></span>  
  
-   <span data-ttu-id="82c99-108">A [ `using` dyrektywy](../../csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82c99-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c99-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82c99-109">See Also</span></span>  
 [<span data-ttu-id="82c99-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="82c99-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="82c99-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="82c99-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
