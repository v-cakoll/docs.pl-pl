---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d5b07617617ac28e4f7f72bc23a96b45a85dff75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047976"
---
# <a name="httplistener"></a><span data-ttu-id="f4b57-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="f4b57-102">HttpListener</span></span>
<span data-ttu-id="f4b57-103"><xref:System.Net.HttpListener> Klasa zapewnia programistyczny, kontrolowany przez program odbiornik protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4b57-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="f4b57-104">Odbiornik jest aktywny przez okres istnienia <xref:System.Net.HttpListener> obiektu i działa w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4b57-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="f4b57-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="f4b57-105">HTTP.SYS</span></span>  
 <span data-ttu-id="f4b57-106"><xref:System.Net.HttpListener> Klasa jest oparta na protokole HTTP. sys, który jest odbiornikiem trybu jądra, który obsługuje cały ruch HTTP dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f4b57-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="f4b57-107">HTTP. sys umożliwia zarządzanie połączeniami, ograniczanie przepustowości i rejestrowanie serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f4b57-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="f4b57-108">Użyj narzędzia `HttpCfg.exe` , aby dodać certyfikaty SSL.</span><span class="sxs-lookup"><span data-stu-id="f4b57-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="f4b57-109">Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą narzędzia [HttpCfg. exe](https://go.microsoft.com/fwlink/?LinkID=178284) w dokumentacji [serwera](https://go.microsoft.com/fwlink/?LinkID=178285) .</span><span class="sxs-lookup"><span data-stu-id="f4b57-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b57-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4b57-110">See also</span></span>

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [<span data-ttu-id="f4b57-111">Serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="f4b57-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)
- [<span data-ttu-id="f4b57-112">Ulepszenia zabezpieczeń w programie Internet Information</span><span class="sxs-lookup"><span data-stu-id="f4b57-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)
- [<span data-ttu-id="f4b57-113">Przykład aplikacji hosta odbiornika HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="f4b57-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)
- [<span data-ttu-id="f4b57-114">Przykład technologii odbiornika HttpListener</span><span class="sxs-lookup"><span data-stu-id="f4b57-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)
- [<span data-ttu-id="f4b57-115">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="f4b57-115">Network Programming Samples</span></span>](network-programming-samples.md)
