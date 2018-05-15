---
title: '&lt;add&gt; w &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 3f1b7e8f1f4ab8542270d459ce5020ce4320eea9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="dfc13-102">&lt;add&gt; w &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="dfc13-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="dfc13-103">Reprezentuje element konfiguracji określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="dfc13-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="dfc13-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dfc13-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dfc13-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="dfc13-105">\<client></span></span>  
<span data-ttu-id="dfc13-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="dfc13-106">\<endpoint></span></span>  
<span data-ttu-id="dfc13-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="dfc13-107">\<host></span></span>  
<span data-ttu-id="dfc13-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="dfc13-108">\<baseAddresses></span></span>  
<span data-ttu-id="dfc13-109">\<Właściwość baseAddress ></span><span class="sxs-lookup"><span data-stu-id="dfc13-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc13-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfc13-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="dfc13-111">Typ</span><span class="sxs-lookup"><span data-stu-id="dfc13-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfc13-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dfc13-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dfc13-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dfc13-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfc13-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dfc13-114">Attributes</span></span>  
  
|<span data-ttu-id="dfc13-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dfc13-115">Attribute</span></span>|<span data-ttu-id="dfc13-116">Opis</span><span class="sxs-lookup"><span data-stu-id="dfc13-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="dfc13-117">Ciąg określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="dfc13-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfc13-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dfc13-118">Child Elements</span></span>  
 <span data-ttu-id="dfc13-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="dfc13-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfc13-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dfc13-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dfc13-121">Element</span><span class="sxs-lookup"><span data-stu-id="dfc13-121">Element</span></span>|<span data-ttu-id="dfc13-122">Opis</span><span class="sxs-lookup"><span data-stu-id="dfc13-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc13-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="dfc13-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="dfc13-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="dfc13-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfc13-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfc13-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="dfc13-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="dfc13-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
