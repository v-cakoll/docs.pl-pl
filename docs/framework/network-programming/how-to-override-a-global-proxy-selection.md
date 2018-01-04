---
title: "Porady: Zastąp wybór globalnych serwera Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 970b428343f4e2dec73e7eceec20414cd8bdfbac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="e7816-102">Porady: Zastąp wybór globalnych serwera Proxy</span><span class="sxs-lookup"><span data-stu-id="e7816-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="e7816-103">W tym przykładzie wysyła **WebRequest** do www.contoso.com zastępujący wybór globalnych serwera proxy z serwerem proxy o nazwie `alternateproxy` na porcie 80.</span><span class="sxs-lookup"><span data-stu-id="e7816-103">This example sends a **WebRequest** to www.contoso.com that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7816-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7816-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7816-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e7816-105">Compiling the Code</span></span>  
 <span data-ttu-id="e7816-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e7816-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e7816-107">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7816-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7816-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7816-108">See Also</span></span>  
 [<span data-ttu-id="e7816-109">Korzystanie z protokołów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e7816-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="e7816-110">Dostęp do Internetu za pośrednictwem serwera proxy</span><span class="sxs-lookup"><span data-stu-id="e7816-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
