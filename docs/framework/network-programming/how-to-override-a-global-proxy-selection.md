---
title: 'Porady: Przesłoń wyboru globalnego serwera Proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 244315b5df4200524685bc5b9fb75a0d7fd9b39e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698357"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="c1485-102">Porady: Przesłoń wyboru globalnego serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="c1485-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="c1485-103">W tym przykładzie wysyła **WebRequest** do `www.contoso.com` , zastępuje wyboru globalnego serwera proxy przy użyciu serwera proxy, o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="c1485-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1485-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1485-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1485-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c1485-105">Compiling the Code</span></span>  
 <span data-ttu-id="c1485-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c1485-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c1485-107">A [ `using` dyrektywy](~/docs/csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c1485-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1485-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1485-108">See Also</span></span>  
 [<span data-ttu-id="c1485-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="c1485-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="c1485-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="c1485-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
