---
title: Wdrażanie usług
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 684b781c568518cfb321d8021e4f7062e855e6aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798141"
---
# <a name="deploying-services"></a><span data-ttu-id="de9d4-102">Wdrażanie usług</span><span class="sxs-lookup"><span data-stu-id="de9d4-102">Deploying Services</span></span>
<span data-ttu-id="de9d4-103">W tym temacie opisano sposób wdrażania aplikacji Windows Communication Foundation (WCF) w środowisku wykonawczym.</span><span class="sxs-lookup"><span data-stu-id="de9d4-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="de9d4-104">Wybieranie środowiska hostingu dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="de9d4-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="de9d4-105">Usługi WCF są przeznaczone do uruchamiania w dowolnym procesie systemu Windows, który obsługuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="de9d4-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="de9d4-106">Aby stał się aktywny, usługa musi być hostowana w środowisku uruchomieniowym, które tworzy go i kontroluje jego kontekst i okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="de9d4-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="de9d4-107">Zakres opcji hostingu od uruchamiania wewnątrz najprostszej aplikacji konsolowej do środowisk serwerowych, takich jak usługa systemu Windows, Internet Information Services (IIS) lub w ramach procesu roboczego zarządzanego przez usługę aktywacji systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="de9d4-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="de9d4-108">Aby zapoznać się z różnymi opcjami hostingu dla aplikacji WCF, zobacz [usługi hostingu](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="de9d4-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9d4-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de9d4-109">See also</span></span>

- [<span data-ttu-id="de9d4-110">Hosting</span><span class="sxs-lookup"><span data-stu-id="de9d4-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="de9d4-111">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="de9d4-111">Hosting Services</span></span>](../hosting-services.md)
