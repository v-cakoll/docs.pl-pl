---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d3fecb9fe78ca54f68d3c5a97dae5d5dd9fbb28d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075421"
---
# <a name="httplistener"></a><span data-ttu-id="e589c-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="e589c-102">HttpListener</span></span>
<span data-ttu-id="e589c-103"><xref:System.Net.HttpListener> Klasa udostępnia programowo kontrolowanego odbiornika protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e589c-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="e589c-104">Odbiornik jest aktywna przez okres istnienia <xref:System.Net.HttpListener> obiektu i jest uruchamiana w ramach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e589c-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="e589c-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="e589c-105">HTTP.SYS</span></span>  
 <span data-ttu-id="e589c-106"><xref:System.Net.HttpListener> Klasy są wbudowane HTTP.sys, czyli odbiornik trybu jądra, który obsługuje cały ruch HTTP dla Windows.</span><span class="sxs-lookup"><span data-stu-id="e589c-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="e589c-107">Sterownik HTTP.sys zapewnia zarządzanie połączeniami, ograniczenie przepustowości i rejestrowanie serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e589c-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="e589c-108">Użyj `HttpCfg.exe` narzędzie, aby dodać certyfikaty SSL.</span><span class="sxs-lookup"><span data-stu-id="e589c-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="e589c-109">Aby uzyskać więcej informacji, zobacz dokumentację na [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) narzędzia w [serwera](https://go.microsoft.com/fwlink/?LinkID=178285) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e589c-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e589c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e589c-110">See also</span></span>

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [<span data-ttu-id="e589c-111">HTTP Server</span><span class="sxs-lookup"><span data-stu-id="e589c-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)
- [<span data-ttu-id="e589c-112">Usprawnienia zabezpieczeń w IIS</span><span class="sxs-lookup"><span data-stu-id="e589c-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)
- [<span data-ttu-id="e589c-113">Przykład aplikacji hosta HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="e589c-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)
- [<span data-ttu-id="e589c-114">Przykład technologii HttpListener</span><span class="sxs-lookup"><span data-stu-id="e589c-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)
- [<span data-ttu-id="e589c-115">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="e589c-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
