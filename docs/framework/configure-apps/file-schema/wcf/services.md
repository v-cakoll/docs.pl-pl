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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb292a62c2b042c387799164ff4cec88bd2ca482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="3ba0a-102">&lt;usługi&gt;</span><span class="sxs-lookup"><span data-stu-id="3ba0a-102">&lt;services&gt;</span></span>
<span data-ttu-id="3ba0a-103">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ba0a-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ba0a-104">Każda usługa ma własną `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ba0a-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="3ba0a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3ba0a-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba0a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ba0a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ba0a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ba0a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3ba0a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ba0a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ba0a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ba0a-109">Attributes</span></span>  
 <span data-ttu-id="3ba0a-110">Brak</span><span class="sxs-lookup"><span data-stu-id="3ba0a-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ba0a-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ba0a-111">Child Elements</span></span>  
  
|<span data-ttu-id="3ba0a-112">Element</span><span class="sxs-lookup"><span data-stu-id="3ba0a-112">Element</span></span>|<span data-ttu-id="3ba0a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3ba0a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ba0a-114">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="3ba0a-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="3ba0a-115">Definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="3ba0a-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ba0a-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ba0a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3ba0a-117">Element</span><span class="sxs-lookup"><span data-stu-id="3ba0a-117">Element</span></span>|<span data-ttu-id="3ba0a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3ba0a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ba0a-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3ba0a-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="3ba0a-120">Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ba0a-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ba0a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ba0a-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
