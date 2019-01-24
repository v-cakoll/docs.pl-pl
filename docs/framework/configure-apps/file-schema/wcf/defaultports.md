---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2c742f98315c0e497ac4117953424bae913cb5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614500"
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="1fe6f-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="1fe6f-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="1fe6f-103">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="1fe6f-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="1fe6f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1fe6f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1fe6f-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1fe6f-105">\<behaviors></span></span>  
<span data-ttu-id="1fe6f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1fe6f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1fe6f-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1fe6f-107">\<behavior></span></span>  
<span data-ttu-id="1fe6f-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="1fe6f-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="1fe6f-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="1fe6f-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe6f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fe6f-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fe6f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fe6f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1fe6f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fe6f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fe6f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fe6f-113">Attributes</span></span>  
 <span data-ttu-id="1fe6f-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="1fe6f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fe6f-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fe6f-115">Child Elements</span></span>  
  
|<span data-ttu-id="1fe6f-116">Element</span><span class="sxs-lookup"><span data-stu-id="1fe6f-116">Element</span></span>|<span data-ttu-id="1fe6f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1fe6f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fe6f-118">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="1fe6f-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="1fe6f-119">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="1fe6f-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fe6f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fe6f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1fe6f-121">Element</span><span class="sxs-lookup"><span data-stu-id="1fe6f-121">Element</span></span>|<span data-ttu-id="1fe6f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1fe6f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fe6f-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="1fe6f-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="1fe6f-124">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="1fe6f-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fe6f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fe6f-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
