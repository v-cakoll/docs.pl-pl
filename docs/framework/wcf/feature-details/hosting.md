---
title: Hosting2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8b0e8aa1dfe2e7a737e88530a206739eef39b2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hosting"></a><span data-ttu-id="a4222-102">Hosting</span><span class="sxs-lookup"><span data-stu-id="a4222-102">Hosting</span></span>
<span data-ttu-id="a4222-103">Tematy w tej sekcji opisano, hostingu usług.</span><span class="sxs-lookup"><span data-stu-id="a4222-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="a4222-104">Usługa może być obsługiwany przez Internet Information Services (IIS), usługa aktywacji procesów systemu Windows (WAS), Windows Server AppFabric, usługa systemu Windows lub aplikacji zarządzanej — ta opcja jest często określany jako *self hosting*.</span><span class="sxs-lookup"><span data-stu-id="a4222-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="a4222-105">Należy zauważyć, że uruchomione usługi lub dowolnego rozszerzenia zabezpieczeń dokonywania niezaufanych hosta.</span><span class="sxs-lookup"><span data-stu-id="a4222-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4222-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a4222-106">In This Section</span></span>  
 [<span data-ttu-id="a4222-107">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="a4222-107">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 <span data-ttu-id="a4222-108">Opisuje sposób [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługa jest obsługiwana przez Internetowe usługi informacyjne lub [systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span><span class="sxs-lookup"><span data-stu-id="a4222-108">Describes how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is hosted in Internet Information Services or [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span></span>  
  
 [<span data-ttu-id="a4222-109">Hosting w usłudze aktywacji procesów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4222-109">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="a4222-110">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana przez usługę aktywacji procesów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a4222-110">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="a4222-111">Hosting w aplikacji usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4222-111">Hosting in a Windows Service Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="a4222-112">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana przez usługę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a4222-112">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="a4222-113">Hosting w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="a4222-113">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 <span data-ttu-id="a4222-114">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4222-114">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="a4222-115">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="a4222-115">Configuration-Based Activation in IIS and WAS</span></span>](../../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="a4222-116">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana w ramach usług IIS lub WAS bez użycia pliku svc.</span><span class="sxs-lookup"><span data-stu-id="a4222-116">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="a4222-117">Obsługa wielu wiązań witryny usług IIS</span><span class="sxs-lookup"><span data-stu-id="a4222-117">Supporting Multiple IIS Site Bindings</span></span>](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="a4222-118">Opisuje sposób określenia wielu adresami podstawowymi dla usługi przy użyciu tego samego schematu identyfikatora URI w jednej witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a4222-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4222-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4222-119">See Also</span></span>  
 [<span data-ttu-id="a4222-120">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="a4222-120">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="a4222-121">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="a4222-121">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
