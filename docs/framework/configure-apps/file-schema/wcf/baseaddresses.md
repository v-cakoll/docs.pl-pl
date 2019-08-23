---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926421"
---
# <a name="baseaddresses"></a><span data-ttu-id="0eee7-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="0eee7-101">\<baseAddresses></span></span>
<span data-ttu-id="0eee7-102">Reprezentuje kolekcję `baseAddress` elementów, które są adresami podstawowymi dla hosta usługi w środowisku własnym.</span><span class="sxs-lookup"><span data-stu-id="0eee7-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="0eee7-103">W przypadku obecności adresu podstawowego punkty końcowe można skonfigurować przy użyciu adresów względnych dla adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="0eee7-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="0eee7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0eee7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0eee7-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="0eee7-105">\<client></span></span>  
<span data-ttu-id="0eee7-106">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="0eee7-106">\<endpoint></span></span>  
<span data-ttu-id="0eee7-107">\<host></span><span class="sxs-lookup"><span data-stu-id="0eee7-107">\<host></span></span>  
<span data-ttu-id="0eee7-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="0eee7-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eee7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0eee7-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="0eee7-110">Typ</span><span class="sxs-lookup"><span data-stu-id="0eee7-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eee7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0eee7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0eee7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0eee7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eee7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0eee7-113">Attributes</span></span>  
 <span data-ttu-id="0eee7-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="0eee7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0eee7-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0eee7-115">Child Elements</span></span>  
  
|<span data-ttu-id="0eee7-116">Element</span><span class="sxs-lookup"><span data-stu-id="0eee7-116">Element</span></span>|<span data-ttu-id="0eee7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0eee7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eee7-118">\<add></span><span class="sxs-lookup"><span data-stu-id="0eee7-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="0eee7-119">Element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="0eee7-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0eee7-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0eee7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0eee7-121">Element</span><span class="sxs-lookup"><span data-stu-id="0eee7-121">Element</span></span>|<span data-ttu-id="0eee7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0eee7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eee7-123">\<host></span><span class="sxs-lookup"><span data-stu-id="0eee7-123">\<host></span></span>](host.md)|<span data-ttu-id="0eee7-124">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="0eee7-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eee7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0eee7-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="0eee7-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="0eee7-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
