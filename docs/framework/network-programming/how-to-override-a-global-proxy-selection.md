---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
description: Postępuj zgodnie z tym przykładem, aby zastąpić globalne Wybieranie serwera proxy przez wysłanie żądania webżądanie do adresu URL, które zastępuje wybór z serwerem proxy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502512"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="4d3ae-103">Instrukcje: zastępowanie wyboru globalnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="4d3ae-103">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="4d3ae-104">W tym przykładzie wysłano **żądanie** sieci webdo `www.contoso.com` , które zastąpi globalny wybór serwera proxy serwerem proxy o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="4d3ae-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d3ae-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d3ae-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d3ae-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4d3ae-106">Compiling the Code</span></span>  
 <span data-ttu-id="4d3ae-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4d3ae-107">This example requires:</span></span>  
  
- <span data-ttu-id="4d3ae-108">[ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) dla przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="4d3ae-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3ae-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d3ae-109">See also</span></span>

- [<span data-ttu-id="4d3ae-110">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="4d3ae-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="4d3ae-111">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="4d3ae-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
