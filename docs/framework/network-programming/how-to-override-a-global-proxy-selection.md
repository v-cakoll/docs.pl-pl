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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800787"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="498bc-102">Porady: Przesłoń wyboru globalnego serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="498bc-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="498bc-103">W tym przykładzie wysyła **WebRequest** do `www.contoso.com` , zastępuje wyboru globalnego serwera proxy przy użyciu serwera proxy, o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="498bc-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="498bc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="498bc-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="498bc-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="498bc-105">Compiling the Code</span></span>  
 <span data-ttu-id="498bc-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="498bc-106">This example requires:</span></span>  
  
-   <span data-ttu-id="498bc-107">A [ `using` dyrektywy](~/docs/csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="498bc-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498bc-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="498bc-108">See Also</span></span>  
 [<span data-ttu-id="498bc-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="498bc-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="498bc-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="498bc-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
