---
title: Wdrażanie usług
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 4d9efcb4da064021d93345285982c0cbd29dde2e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803585"
---
# <a name="deploying-services"></a><span data-ttu-id="38f28-102">Wdrażanie usług</span><span class="sxs-lookup"><span data-stu-id="38f28-102">Deploying Services</span></span>
<span data-ttu-id="38f28-103">W tym temacie opisano, jak można wdrożyć aplikację systemu Windows Communication Foundation (WCF) w środowisku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="38f28-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="38f28-104">Wybieranie środowiska macierzystego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="38f28-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="38f28-105">Usługi WCF zostały zaprojektowane do uruchamiania w dowolnym procesie systemu Windows obsługuje kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="38f28-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="38f28-106">Staje się aktywny, usługa musi być hostowany w środowisku czasu wykonywania, która tworzy go i kontroluje jego kontekstu i okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="38f28-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="38f28-107">Hosting zakres opcje uruchamiania wewnątrz najprostszym aplikacji konsoli do środowiska serwera, takich jak usługi systemu Windows, Internet Information Services (IIS), lub w ramach procesu roboczego zarządzane przez usługę aktywacji systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="38f28-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="38f28-108">Aby zapoznać się z różnych opcji hostingu aplikacji WCF, zobacz [Hosting usług](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="38f28-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f28-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38f28-109">See Also</span></span>  
 [<span data-ttu-id="38f28-110">Hosting</span><span class="sxs-lookup"><span data-stu-id="38f28-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="38f28-111">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="38f28-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
