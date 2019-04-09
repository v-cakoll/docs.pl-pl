---
title: Wdrażanie usług
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 2c3cd17b597fafcd02b9155089bc583fafbc9dea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085766"
---
# <a name="deploying-services"></a><span data-ttu-id="2ed6a-102">Wdrażanie usług</span><span class="sxs-lookup"><span data-stu-id="2ed6a-102">Deploying Services</span></span>
<span data-ttu-id="2ed6a-103">W tym temacie opisano, jak wdrożyć aplikację Windows Communication Foundation (WCF) do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2ed6a-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="2ed6a-104">Wybierając Środowisko hostingu aplikacji</span><span class="sxs-lookup"><span data-stu-id="2ed6a-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="2ed6a-105">Usługi WCF są przeznaczone do uruchamiania w każdym procesie Windows obsługuje kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2ed6a-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="2ed6a-106">Stanie się aktywna, usługa musi być hostowany w środowisku uruchomieniowym, tworzy go, która określa jego kontekstu i okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="2ed6a-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="2ed6a-107">Opcje z zakresu od działa wewnątrz najprostszej aplikacji konsoli w środowiskach serwera, takich jak usługa Windows Internet Information Services (IIS) lub w ramach procesu roboczego obsługującego zarządzanych przez Windows Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="2ed6a-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="2ed6a-108">Aby zapoznać się z różnych opcji obsługi aplikacji WCF, zobacz [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="2ed6a-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed6a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ed6a-109">See also</span></span>

- [<span data-ttu-id="2ed6a-110">Hosting</span><span class="sxs-lookup"><span data-stu-id="2ed6a-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="2ed6a-111">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="2ed6a-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
