---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168080"
---
# <a name="services"></a><span data-ttu-id="91f28-101">\<services></span><span class="sxs-lookup"><span data-stu-id="91f28-101">\<services></span></span>
<span data-ttu-id="91f28-102">Usługi są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91f28-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="91f28-103">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91f28-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="91f28-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="91f28-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f28-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="91f28-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91f28-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91f28-106">Attributes and Elements</span></span>  
 <span data-ttu-id="91f28-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91f28-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91f28-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91f28-108">Attributes</span></span>  
 <span data-ttu-id="91f28-109">Brak</span><span class="sxs-lookup"><span data-stu-id="91f28-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91f28-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91f28-110">Child Elements</span></span>  
  
|<span data-ttu-id="91f28-111">Element</span><span class="sxs-lookup"><span data-stu-id="91f28-111">Element</span></span>|<span data-ttu-id="91f28-112">Opis</span><span class="sxs-lookup"><span data-stu-id="91f28-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91f28-113">\<service></span><span class="sxs-lookup"><span data-stu-id="91f28-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="91f28-114">Definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="91f28-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91f28-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91f28-115">Parent Elements</span></span>  
  
|<span data-ttu-id="91f28-116">Element</span><span class="sxs-lookup"><span data-stu-id="91f28-116">Element</span></span>|<span data-ttu-id="91f28-117">Opis</span><span class="sxs-lookup"><span data-stu-id="91f28-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91f28-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="91f28-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="91f28-119">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="91f28-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91f28-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91f28-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
