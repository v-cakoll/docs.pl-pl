---
title: "&lt;usługi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca55770da8da0fe91a12aeb5fa72e61d6dcd67ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="e87dd-102">&lt;usługi&gt;</span><span class="sxs-lookup"><span data-stu-id="e87dd-102">&lt;services&gt;</span></span>
<span data-ttu-id="e87dd-103">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e87dd-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e87dd-104">Każda usługa ma własną `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e87dd-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="e87dd-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e87dd-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87dd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e87dd-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e87dd-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e87dd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e87dd-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e87dd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e87dd-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e87dd-109">Attributes</span></span>  
 <span data-ttu-id="e87dd-110">Brak</span><span class="sxs-lookup"><span data-stu-id="e87dd-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e87dd-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e87dd-111">Child Elements</span></span>  
  
|<span data-ttu-id="e87dd-112">Element</span><span class="sxs-lookup"><span data-stu-id="e87dd-112">Element</span></span>|<span data-ttu-id="e87dd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e87dd-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e87dd-114">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="e87dd-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="e87dd-115">Definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="e87dd-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e87dd-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e87dd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e87dd-117">Element</span><span class="sxs-lookup"><span data-stu-id="e87dd-117">Element</span></span>|<span data-ttu-id="e87dd-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e87dd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e87dd-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e87dd-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e87dd-120">Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e87dd-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e87dd-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e87dd-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
