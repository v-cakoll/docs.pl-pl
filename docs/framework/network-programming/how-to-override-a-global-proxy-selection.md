---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048272"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="90506-102">Instrukcje: zastępowanie wyboru globalnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="90506-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="90506-103">W tym przykładzie wysyła **WebRequest** do `www.contoso.com` który zastępuje wybór `alternateproxy` globalnego serwera proxy z serwera proxy o nazwie na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="90506-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90506-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="90506-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90506-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="90506-105">Compiling the Code</span></span>  
 <span data-ttu-id="90506-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="90506-106">This example requires:</span></span>  
  
- <span data-ttu-id="90506-107">[ `using` Dyrektywa](../../csharp/language-reference/keywords/using-directive.md) dla **System.Net** obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="90506-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90506-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90506-108">See also</span></span>

- [<span data-ttu-id="90506-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="90506-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="90506-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="90506-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
