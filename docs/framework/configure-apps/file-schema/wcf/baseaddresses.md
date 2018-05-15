---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 8de962cc70e1399dd1e9459473055651f9aca5fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="a8eb8-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="a8eb8-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="a8eb8-103">Reprezentuje kolekcję `baseAddress` elementów, które są adresami podstawowymi dla usługi hosta w swoim środowisku.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="a8eb8-104">Jeśli adres podstawowy jest obecny, można skonfigurować punkty końcowe z adresami względem adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="a8eb8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8eb8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8eb8-106">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="a8eb8-106">\<client></span></span>  
<span data-ttu-id="a8eb8-107">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="a8eb8-107">\<endpoint></span></span>  
<span data-ttu-id="a8eb8-108">\<host ></span><span class="sxs-lookup"><span data-stu-id="a8eb8-108">\<host></span></span>  
<span data-ttu-id="a8eb8-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="a8eb8-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8eb8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8eb8-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="a8eb8-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a8eb8-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8eb8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a8eb8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a8eb8-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8eb8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a8eb8-114">Attributes</span></span>  
 <span data-ttu-id="a8eb8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8eb8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a8eb8-116">Child Elements</span></span>  
  
|<span data-ttu-id="a8eb8-117">Element</span><span class="sxs-lookup"><span data-stu-id="a8eb8-117">Element</span></span>|<span data-ttu-id="a8eb8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a8eb8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8eb8-119">\<add></span><span class="sxs-lookup"><span data-stu-id="a8eb8-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="a8eb8-120">Element konfiguracji określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8eb8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a8eb8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a8eb8-122">Element</span><span class="sxs-lookup"><span data-stu-id="a8eb8-122">Element</span></span>|<span data-ttu-id="a8eb8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a8eb8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8eb8-124">\<host ></span><span class="sxs-lookup"><span data-stu-id="a8eb8-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="a8eb8-125">Element konfiguracji określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="a8eb8-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8eb8-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8eb8-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="a8eb8-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="a8eb8-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
