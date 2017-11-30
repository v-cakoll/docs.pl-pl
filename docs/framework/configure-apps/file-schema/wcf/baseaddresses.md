---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bf698b64b528b0ea109223a2d94e6725c8ce6b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="287c7-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="287c7-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="287c7-103">Reprezentuje kolekcję `baseAddress` elementów, które są adresami podstawowymi dla usługi hosta w swoim środowisku.</span><span class="sxs-lookup"><span data-stu-id="287c7-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="287c7-104">Jeśli adres podstawowy jest obecny, można skonfigurować punkty końcowe z adresami względem adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="287c7-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="287c7-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="287c7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="287c7-106">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="287c7-106">\<client></span></span>  
<span data-ttu-id="287c7-107">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="287c7-107">\<endpoint></span></span>  
<span data-ttu-id="287c7-108">\<host ></span><span class="sxs-lookup"><span data-stu-id="287c7-108">\<host></span></span>  
<span data-ttu-id="287c7-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="287c7-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287c7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="287c7-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="287c7-111">Typ</span><span class="sxs-lookup"><span data-stu-id="287c7-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="287c7-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="287c7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="287c7-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="287c7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="287c7-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="287c7-114">Attributes</span></span>  
 <span data-ttu-id="287c7-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="287c7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="287c7-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="287c7-116">Child Elements</span></span>  
  
|<span data-ttu-id="287c7-117">Element</span><span class="sxs-lookup"><span data-stu-id="287c7-117">Element</span></span>|<span data-ttu-id="287c7-118">Opis</span><span class="sxs-lookup"><span data-stu-id="287c7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="287c7-119">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="287c7-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="287c7-120">Element konfiguracji określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="287c7-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="287c7-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="287c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="287c7-122">Element</span><span class="sxs-lookup"><span data-stu-id="287c7-122">Element</span></span>|<span data-ttu-id="287c7-123">Opis</span><span class="sxs-lookup"><span data-stu-id="287c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="287c7-124">\<host ></span><span class="sxs-lookup"><span data-stu-id="287c7-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="287c7-125">Element konfiguracji określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="287c7-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="287c7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="287c7-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="287c7-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="287c7-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
