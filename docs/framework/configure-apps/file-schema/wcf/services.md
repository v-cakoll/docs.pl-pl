---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 4dc425fa97eaf99664f0d9bbbbc851c462cbf373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274966"
---
# <a name="services"></a><span data-ttu-id="60abc-101">\<services></span><span class="sxs-lookup"><span data-stu-id="60abc-101">\<services></span></span>
<span data-ttu-id="60abc-102">Usługi są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="60abc-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="60abc-103">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="60abc-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="60abc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60abc-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60abc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="60abc-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60abc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="60abc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="60abc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="60abc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60abc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="60abc-108">Attributes</span></span>  
 <span data-ttu-id="60abc-109">Brak</span><span class="sxs-lookup"><span data-stu-id="60abc-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60abc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="60abc-110">Child Elements</span></span>  
  
|<span data-ttu-id="60abc-111">Element</span><span class="sxs-lookup"><span data-stu-id="60abc-111">Element</span></span>|<span data-ttu-id="60abc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="60abc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60abc-113">\<service></span><span class="sxs-lookup"><span data-stu-id="60abc-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="60abc-114">Definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="60abc-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60abc-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="60abc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="60abc-116">Element</span><span class="sxs-lookup"><span data-stu-id="60abc-116">Element</span></span>|<span data-ttu-id="60abc-117">Opis</span><span class="sxs-lookup"><span data-stu-id="60abc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60abc-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60abc-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="60abc-119">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="60abc-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60abc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60abc-120">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
