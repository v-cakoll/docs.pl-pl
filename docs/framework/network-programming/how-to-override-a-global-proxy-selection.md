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
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="db6c8-102">Instrukcje: zastępowanie wyboru globalnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="db6c8-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="db6c8-103">W tym przykładzie wysłano **żądanie** sieci `www.contoso.com` webdo, które zastąpi globalny wybór serwera proxy `alternateproxy` serwerem proxy o nazwie na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="db6c8-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db6c8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="db6c8-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db6c8-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="db6c8-105">Compiling the Code</span></span>  
 <span data-ttu-id="db6c8-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="db6c8-106">This example requires:</span></span>  
  
- <span data-ttu-id="db6c8-107">Dyrektywa dla przestrzeni nazw **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="db6c8-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6c8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db6c8-108">See also</span></span>

- [<span data-ttu-id="db6c8-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="db6c8-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="db6c8-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="db6c8-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
