---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db2c42dab15b4282c5474c50f970ffe47a101215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393455"
---
# <a name="httplistener"></a><span data-ttu-id="ba7e4-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="ba7e4-102">HttpListener</span></span>
<span data-ttu-id="ba7e4-103"><xref:System.Net.HttpListener> Klasa udostępnia programowo kontrolowane odbiornika protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="ba7e4-104">Odbiornik jest aktywne przez czas ich istnienia <xref:System.Net.HttpListener> obiektu i działa w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="ba7e4-105">PROTOKÓŁ HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="ba7e4-105">HTTP.SYS</span></span>  
 <span data-ttu-id="ba7e4-106"><xref:System.Net.HttpListener> Klasy jest oparty na HTTP.sys, który jest odbiornik trybu jądra, który obsługuje cały ruch HTTP dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="ba7e4-107">Składnik HTTP.sys zapewnia zarządzanie połączeniami, przepustowości i rejestrowanie serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="ba7e4-108">Użyj `HttpCfg.exe` narzędzia, aby dodać certyfikaty SSL.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="ba7e4-109">Aby uzyskać więcej informacji, zobacz dokumentację na [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) narzędzie w [serwera](http://go.microsoft.com/fwlink/?LinkID=178285) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ba7e4-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7e4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba7e4-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="ba7e4-111">Serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="ba7e4-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="ba7e4-112">Ulepszenia zabezpieczeń programu Internet Information</span><span class="sxs-lookup"><span data-stu-id="ba7e4-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="ba7e4-113">Przykład aplikacji hosta HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="ba7e4-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="ba7e4-114">Przykładowe technologii HttpListener</span><span class="sxs-lookup"><span data-stu-id="ba7e4-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="ba7e4-115">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="ba7e4-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
