---
title: 'Instrukcje: Zastąp wyboru globalnego serwera Proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 6973503f12e0e60ee139c5cd7da09ab319d70218
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592127"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="343fc-102">Instrukcje: Zastąp wyboru globalnego serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="343fc-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="343fc-103">W tym przykładzie wysyła **WebRequest** do `www.contoso.com` , zastępuje wyboru globalnego serwera proxy przy użyciu serwera proxy, o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="343fc-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="343fc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="343fc-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="343fc-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="343fc-105">Compiling the Code</span></span>  
 <span data-ttu-id="343fc-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="343fc-106">This example requires:</span></span>  
  
-   <span data-ttu-id="343fc-107">A [ `using` dyrektywy](~/docs/csharp/language-reference/keywords/using-directive.md) dla **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="343fc-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343fc-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="343fc-108">See also</span></span>
- [<span data-ttu-id="343fc-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="343fc-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="343fc-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="343fc-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
