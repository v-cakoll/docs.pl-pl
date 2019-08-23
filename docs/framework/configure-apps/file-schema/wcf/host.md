---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918708"
---
# <a name="host"></a><span data-ttu-id="ae587-101">\<host></span><span class="sxs-lookup"><span data-stu-id="ae587-101">\<host></span></span>
<span data-ttu-id="ae587-102">Określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ae587-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="ae587-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae587-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae587-104">\<> usług</span><span class="sxs-lookup"><span data-stu-id="ae587-104">\<services></span></span>  
<span data-ttu-id="ae587-105">\<service></span><span class="sxs-lookup"><span data-stu-id="ae587-105">\<service></span></span>  
<span data-ttu-id="ae587-106">\<host></span><span class="sxs-lookup"><span data-stu-id="ae587-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae587-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae587-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="ae587-108">Typ</span><span class="sxs-lookup"><span data-stu-id="ae587-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae587-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae587-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae587-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae587-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae587-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae587-111">Attributes</span></span>  
 <span data-ttu-id="ae587-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae587-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae587-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae587-113">Child Elements</span></span>  
  
|<span data-ttu-id="ae587-114">Element</span><span class="sxs-lookup"><span data-stu-id="ae587-114">Element</span></span>|<span data-ttu-id="ae587-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ae587-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae587-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="ae587-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="ae587-117">Kolekcja `baseAddress` elementów, która określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ae587-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="ae587-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="ae587-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="ae587-119">Element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ae587-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae587-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae587-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ae587-121">Element</span><span class="sxs-lookup"><span data-stu-id="ae587-121">Element</span></span>|<span data-ttu-id="ae587-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ae587-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae587-123">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="ae587-123">\<service></span></span>](service.md)|<span data-ttu-id="ae587-124">Określa ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ae587-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae587-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae587-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ae587-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="ae587-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
