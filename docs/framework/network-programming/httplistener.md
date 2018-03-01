---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b4b8c1e916aa9382d156a197fa15c2e72e900a1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="httplistener"></a><span data-ttu-id="f5933-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="f5933-102">HttpListener</span></span>
<span data-ttu-id="f5933-103"><xref:System.Net.HttpListener> Klasa udostępnia programowo kontrolowane odbiornika protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5933-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="f5933-104">Odbiornik jest aktywne przez czas ich istnienia <xref:System.Net.HttpListener> obiektu i działa w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5933-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="f5933-105">PROTOKÓŁ HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="f5933-105">HTTP.SYS</span></span>  
 <span data-ttu-id="f5933-106"><xref:System.Net.HttpListener> Klasy jest oparty na HTTP.sys, który jest odbiornik trybu jądra, który obsługuje cały ruch HTTP dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f5933-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="f5933-107">Składnik HTTP.sys zapewnia zarządzanie połączeniami, przepustowości i rejestrowanie serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f5933-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="f5933-108">Użyj `HttpCfg.exe` narzędzia, aby dodać certyfikaty SSL.</span><span class="sxs-lookup"><span data-stu-id="f5933-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="f5933-109">Aby uzyskać więcej informacji, zobacz dokumentację na [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) narzędzie w [serwera](http://go.microsoft.com/fwlink/?LinkID=178285) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f5933-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5933-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5933-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="f5933-111">Serwer HTTP</span><span class="sxs-lookup"><span data-stu-id="f5933-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="f5933-112">Ulepszenia zabezpieczeń programu Internet Information</span><span class="sxs-lookup"><span data-stu-id="f5933-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="f5933-113">Przykład aplikacji hosta HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="f5933-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="f5933-114">Przykładowe technologii HttpListener</span><span class="sxs-lookup"><span data-stu-id="f5933-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="f5933-115">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="f5933-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
