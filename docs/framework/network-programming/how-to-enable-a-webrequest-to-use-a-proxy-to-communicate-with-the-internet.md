---
title: 'Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048297"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="415b8-102">Instrukcje: włączanie korzystania z serwera proxy do komunikacji z Internetem przez element WebRequest</span><span class="sxs-lookup"><span data-stu-id="415b8-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="415b8-103">Ten przykład tworzy globalne wystąpienie serwera proxy, które umożliwi <xref:System.Net.WebRequest> korzystanie z serwera proxy do komunikowania się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="415b8-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="415b8-104">W przykładzie przyjęto założenie, że serwer `webproxy` proxy ma nazwę i komunikuje się z portem 80, standardowy port HTTP.</span><span class="sxs-lookup"><span data-stu-id="415b8-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415b8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="415b8-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="415b8-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="415b8-106">Compiling the Code</span></span>  
 <span data-ttu-id="415b8-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="415b8-107">This example requires:</span></span>  
  
- <span data-ttu-id="415b8-108">Dyrektywa dla przestrzeni nazw **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="415b8-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415b8-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="415b8-109">See also</span></span>

- [<span data-ttu-id="415b8-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="415b8-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="415b8-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="415b8-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
