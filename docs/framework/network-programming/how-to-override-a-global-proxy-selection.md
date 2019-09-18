---
title: 'Instrukcje: zastępowanie wyboru globalnego serwera proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048272"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="9ab15-102">Instrukcje: zastępowanie wyboru globalnego serwera proxy</span><span class="sxs-lookup"><span data-stu-id="9ab15-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="9ab15-103">W tym przykładzie wysłano **żądanie** sieci `www.contoso.com` webdo, które zastąpi globalny wybór serwera proxy `alternateproxy` serwerem proxy o nazwie na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="9ab15-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab15-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ab15-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ab15-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9ab15-105">Compiling the Code</span></span>  
 <span data-ttu-id="9ab15-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9ab15-106">This example requires:</span></span>  
  
- <span data-ttu-id="9ab15-107">Dyrektywa dla przestrzeni nazw **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="9ab15-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab15-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ab15-108">See also</span></span>

- [<span data-ttu-id="9ab15-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="9ab15-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="9ab15-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="9ab15-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
