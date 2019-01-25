---
title: '&lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 34d400e74b24e9eb4140d1b43597b0217b23d80c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730129"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="0fcb9-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="0fcb9-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="0fcb9-103">Reprezentuje kolekcję `baseAddress` elementy, które są adresami podstawowymi dla usługi hosta w środowisku.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="0fcb9-104">Jeśli adres podstawowy jest obecny, można skonfigurować punkty końcowe z adresami określany względem adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="0fcb9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fcb9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fcb9-106">\<client></span><span class="sxs-lookup"><span data-stu-id="0fcb9-106">\<client></span></span>  
<span data-ttu-id="0fcb9-107">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="0fcb9-107">\<endpoint></span></span>  
<span data-ttu-id="0fcb9-108">\<host></span><span class="sxs-lookup"><span data-stu-id="0fcb9-108">\<host></span></span>  
<span data-ttu-id="0fcb9-109">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="0fcb9-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fcb9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fcb9-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="0fcb9-111">Typ</span><span class="sxs-lookup"><span data-stu-id="0fcb9-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fcb9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0fcb9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0fcb9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fcb9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0fcb9-114">Attributes</span></span>  
 <span data-ttu-id="0fcb9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fcb9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0fcb9-116">Child Elements</span></span>  
  
|<span data-ttu-id="0fcb9-117">Element</span><span class="sxs-lookup"><span data-stu-id="0fcb9-117">Element</span></span>|<span data-ttu-id="0fcb9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0fcb9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fcb9-119">\<add></span><span class="sxs-lookup"><span data-stu-id="0fcb9-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="0fcb9-120">Element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fcb9-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0fcb9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0fcb9-122">Element</span><span class="sxs-lookup"><span data-stu-id="0fcb9-122">Element</span></span>|<span data-ttu-id="0fcb9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="0fcb9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fcb9-124">\<host></span><span class="sxs-lookup"><span data-stu-id="0fcb9-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="0fcb9-125">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="0fcb9-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fcb9-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fcb9-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="0fcb9-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="0fcb9-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
