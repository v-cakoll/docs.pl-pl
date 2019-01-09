---
title: '&lt;Usługi&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: a48bd0ac30c1a85602122b2fd9213c2aa5159e91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148100"
---
# <a name="ltservicesgt"></a><span data-ttu-id="b833c-102">&lt;Usługi&gt;</span><span class="sxs-lookup"><span data-stu-id="b833c-102">&lt;services&gt;</span></span>
<span data-ttu-id="b833c-103">Usługi są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b833c-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="b833c-104">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b833c-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="b833c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b833c-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b833c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b833c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b833c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b833c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b833c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b833c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b833c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b833c-109">Attributes</span></span>  
 <span data-ttu-id="b833c-110">Brak</span><span class="sxs-lookup"><span data-stu-id="b833c-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b833c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b833c-111">Child Elements</span></span>  
  
|<span data-ttu-id="b833c-112">Element</span><span class="sxs-lookup"><span data-stu-id="b833c-112">Element</span></span>|<span data-ttu-id="b833c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b833c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b833c-114">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="b833c-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="b833c-115">Definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="b833c-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b833c-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b833c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b833c-117">Element</span><span class="sxs-lookup"><span data-stu-id="b833c-117">Element</span></span>|<span data-ttu-id="b833c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b833c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b833c-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b833c-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="b833c-120">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b833c-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b833c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b833c-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
