---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: c00d5fe3e8b2ba05843e09aca6aaa79386541bad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937201"
---
# <a name="services"></a><span data-ttu-id="c4948-101">\<> usług</span><span class="sxs-lookup"><span data-stu-id="c4948-101">\<services></span></span>
<span data-ttu-id="c4948-102">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4948-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="c4948-103">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="c4948-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="c4948-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4948-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4948-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4948-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4948-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c4948-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c4948-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c4948-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4948-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c4948-108">Attributes</span></span>  
 <span data-ttu-id="c4948-109">Brak</span><span class="sxs-lookup"><span data-stu-id="c4948-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4948-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c4948-110">Child Elements</span></span>  
  
|<span data-ttu-id="c4948-111">Element</span><span class="sxs-lookup"><span data-stu-id="c4948-111">Element</span></span>|<span data-ttu-id="c4948-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c4948-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4948-113">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="c4948-113">\<service></span></span>](service.md)|<span data-ttu-id="c4948-114">Zdefiniuj kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="c4948-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4948-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c4948-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c4948-116">Element</span><span class="sxs-lookup"><span data-stu-id="c4948-116">Element</span></span>|<span data-ttu-id="c4948-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c4948-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4948-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c4948-118">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="c4948-119">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c4948-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4948-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4948-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
