---
title: 'Porady: Przesłoń wyboru globalnego serwera Proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2be271123e34f155a79269d3b810c50fe24a40c6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849935"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="2d9b3-102">Porady: Przesłoń wyboru globalnego serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="2d9b3-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="2d9b3-103">W tym przykładzie wysyła **WebRequest** do `www.contoso.com` , zastępuje wyboru globalnego serwera proxy przy użyciu serwera proxy, o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="2d9b3-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d9b3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d9b3-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d9b3-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2d9b3-105">Compiling the Code</span></span>  
 <span data-ttu-id="2d9b3-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2d9b3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2d9b3-107">A [ `using` dyrektywy](~/docs/csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2d9b3-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9b3-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d9b3-108">See Also</span></span>  
 [<span data-ttu-id="2d9b3-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="2d9b3-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="2d9b3-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="2d9b3-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
