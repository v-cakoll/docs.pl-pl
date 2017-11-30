---
title: '&lt;add&gt; w &lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="e50da-102">&lt;add&gt; w &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="e50da-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="e50da-103">Reprezentuje element konfiguracji określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e50da-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="e50da-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e50da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e50da-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="e50da-105">\<client></span></span>  
<span data-ttu-id="e50da-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="e50da-106">\<endpoint></span></span>  
<span data-ttu-id="e50da-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="e50da-107">\<host></span></span>  
<span data-ttu-id="e50da-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e50da-108">\<baseAddresses></span></span>  
<span data-ttu-id="e50da-109">\<Właściwość baseAddress ></span><span class="sxs-lookup"><span data-stu-id="e50da-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50da-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e50da-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="e50da-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e50da-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e50da-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e50da-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e50da-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e50da-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e50da-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e50da-114">Attributes</span></span>  
  
|<span data-ttu-id="e50da-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e50da-115">Attribute</span></span>|<span data-ttu-id="e50da-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e50da-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="e50da-117">Ciąg określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e50da-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e50da-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e50da-118">Child Elements</span></span>  
 <span data-ttu-id="e50da-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="e50da-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e50da-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e50da-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e50da-121">Element</span><span class="sxs-lookup"><span data-stu-id="e50da-121">Element</span></span>|<span data-ttu-id="e50da-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e50da-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e50da-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e50da-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="e50da-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="e50da-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e50da-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e50da-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="e50da-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="e50da-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
