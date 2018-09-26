---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0d5b7fccdac9dba3fd44d12241dd60cbaefa1b7a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192943"
---
# <a name="httplistener"></a><span data-ttu-id="7e6c4-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="7e6c4-102">HttpListener</span></span>
<span data-ttu-id="7e6c4-103"><xref:System.Net.HttpListener> Klasa udostępnia programowo kontrolowanego odbiornika protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="7e6c4-104">Odbiornik jest aktywna przez okres istnienia <xref:System.Net.HttpListener> obiektu i jest uruchamiana w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="7e6c4-105">PROTOKÓŁ HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="7e6c4-105">HTTP.SYS</span></span>  
 <span data-ttu-id="7e6c4-106"><xref:System.Net.HttpListener> Klasy są wbudowane HTTP.sys, czyli odbiornik trybu jądra, który obsługuje cały ruch HTTP dla Windows.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="7e6c4-107">Sterownik HTTP.sys zapewnia zarządzanie połączeniami, ograniczenie przepustowości i rejestrowanie serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="7e6c4-108">Użyj `HttpCfg.exe` narzędzie, aby dodać certyfikaty SSL.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="7e6c4-109">Aby uzyskać więcej informacji, zobacz dokumentację na [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) narzędzia w [serwera](https://go.microsoft.com/fwlink/?LinkID=178285) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="7e6c4-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6c4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e6c4-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="7e6c4-111">Serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="7e6c4-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="7e6c4-112">Usprawnienia zabezpieczeń w IIS</span><span class="sxs-lookup"><span data-stu-id="7e6c4-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="7e6c4-113">Przykład aplikacji hosta HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="7e6c4-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="7e6c4-114">Przykład technologii HttpListener</span><span class="sxs-lookup"><span data-stu-id="7e6c4-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="7e6c4-115">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="7e6c4-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
