---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854980"
---
# <a name="services"></a><span data-ttu-id="62fdb-101">\<> usług</span><span class="sxs-lookup"><span data-stu-id="62fdb-101">\<services></span></span>
<span data-ttu-id="62fdb-102">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62fdb-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="62fdb-103">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="62fdb-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="62fdb-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62fdb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62fdb-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62fdb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62fdb-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> usług**</span><span class="sxs-lookup"><span data-stu-id="62fdb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62fdb-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="62fdb-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62fdb-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62fdb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="62fdb-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62fdb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62fdb-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62fdb-110">Attributes</span></span>  
 <span data-ttu-id="62fdb-111">Brak</span><span class="sxs-lookup"><span data-stu-id="62fdb-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62fdb-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62fdb-112">Child Elements</span></span>  
  
|<span data-ttu-id="62fdb-113">Element</span><span class="sxs-lookup"><span data-stu-id="62fdb-113">Element</span></span>|<span data-ttu-id="62fdb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62fdb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62fdb-115">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="62fdb-115">\<service></span></span>](service.md)|<span data-ttu-id="62fdb-116">Zdefiniuj kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="62fdb-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62fdb-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62fdb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="62fdb-118">Element</span><span class="sxs-lookup"><span data-stu-id="62fdb-118">Element</span></span>|<span data-ttu-id="62fdb-119">Opis</span><span class="sxs-lookup"><span data-stu-id="62fdb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62fdb-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="62fdb-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="62fdb-121">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="62fdb-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62fdb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62fdb-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
