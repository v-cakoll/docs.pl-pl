---
title: '&lt;add&gt; w &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149088"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="d1bf1-102">&lt;add&gt; w &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bf1-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="d1bf1-103">Reprezentuje element konfiguracji określający adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="d1bf1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1bf1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1bf1-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-105">\<client></span></span>  
<span data-ttu-id="d1bf1-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-106">\<endpoint></span></span>  
<span data-ttu-id="d1bf1-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-107">\<host></span></span>  
<span data-ttu-id="d1bf1-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-108">\<baseAddresses></span></span>  
<span data-ttu-id="d1bf1-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bf1-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1bf1-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="d1bf1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d1bf1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1bf1-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d1bf1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d1bf1-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1bf1-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1bf1-114">Attributes</span></span>  
  
|<span data-ttu-id="d1bf1-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d1bf1-115">Attribute</span></span>|<span data-ttu-id="d1bf1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d1bf1-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="d1bf1-117">Ciąg, który określa adres bazowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1bf1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d1bf1-118">Child Elements</span></span>  
 <span data-ttu-id="d1bf1-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1bf1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d1bf1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d1bf1-121">Element</span><span class="sxs-lookup"><span data-stu-id="d1bf1-121">Element</span></span>|<span data-ttu-id="d1bf1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d1bf1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1bf1-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="d1bf1-124">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1bf1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1bf1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="d1bf1-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="d1bf1-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
