---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: dc4b31e729f9037da101bdf3e6cde28e91b1a070
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277020"
---
# <a name="baseaddresses"></a><span data-ttu-id="b8b83-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="b8b83-101">\<baseAddresses></span></span>
<span data-ttu-id="b8b83-102">Reprezentuje kolekcję `baseAddress` elementy, które są adresami podstawowymi dla usługi hosta w środowisku.</span><span class="sxs-lookup"><span data-stu-id="b8b83-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="b8b83-103">Jeśli adres podstawowy jest obecny, można skonfigurować punkty końcowe z adresami określany względem adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b8b83-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="b8b83-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8b83-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8b83-105">\<client></span><span class="sxs-lookup"><span data-stu-id="b8b83-105">\<client></span></span>  
<span data-ttu-id="b8b83-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="b8b83-106">\<endpoint></span></span>  
<span data-ttu-id="b8b83-107">\<host></span><span class="sxs-lookup"><span data-stu-id="b8b83-107">\<host></span></span>  
<span data-ttu-id="b8b83-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="b8b83-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b83-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8b83-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="b8b83-110">Typ</span><span class="sxs-lookup"><span data-stu-id="b8b83-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8b83-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8b83-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b8b83-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b8b83-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8b83-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8b83-113">Attributes</span></span>  
 <span data-ttu-id="b8b83-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8b83-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8b83-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8b83-115">Child Elements</span></span>  
  
|<span data-ttu-id="b8b83-116">Element</span><span class="sxs-lookup"><span data-stu-id="b8b83-116">Element</span></span>|<span data-ttu-id="b8b83-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b8b83-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b83-118">\<add></span><span class="sxs-lookup"><span data-stu-id="b8b83-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="b8b83-119">Element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="b8b83-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8b83-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8b83-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b8b83-121">Element</span><span class="sxs-lookup"><span data-stu-id="b8b83-121">Element</span></span>|<span data-ttu-id="b8b83-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b8b83-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b83-123">\<host></span><span class="sxs-lookup"><span data-stu-id="b8b83-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="b8b83-124">Element konfiguracji, który określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="b8b83-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8b83-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8b83-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="b8b83-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="b8b83-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
