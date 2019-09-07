---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 1f9cb6c95fa14a5b8a55cc561699e2a07e1dc80c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399594"
---
# <a name="services"></a><span data-ttu-id="a55cd-101">\<> usług</span><span class="sxs-lookup"><span data-stu-id="a55cd-101">\<services></span></span>
<span data-ttu-id="a55cd-102">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a55cd-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a55cd-103">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="a55cd-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="a55cd-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a55cd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a55cd-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a55cd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a55cd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> usług**</span><span class="sxs-lookup"><span data-stu-id="a55cd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
## <a name="syntax"></a><span data-ttu-id="a55cd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a55cd-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a55cd-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a55cd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a55cd-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a55cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a55cd-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a55cd-110">Attributes</span></span>  
 <span data-ttu-id="a55cd-111">Brak</span><span class="sxs-lookup"><span data-stu-id="a55cd-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a55cd-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a55cd-112">Child Elements</span></span>  
  
|<span data-ttu-id="a55cd-113">Element</span><span class="sxs-lookup"><span data-stu-id="a55cd-113">Element</span></span>|<span data-ttu-id="a55cd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a55cd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55cd-115">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="a55cd-115">\<service></span></span>](service.md)|<span data-ttu-id="a55cd-116">Zdefiniuj kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="a55cd-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a55cd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a55cd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a55cd-118">Element</span><span class="sxs-lookup"><span data-stu-id="a55cd-118">Element</span></span>|<span data-ttu-id="a55cd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a55cd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55cd-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a55cd-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="a55cd-121">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a55cd-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a55cd-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a55cd-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
