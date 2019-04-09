---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130627"
---
# <a name="defaultports"></a><span data-ttu-id="89c1f-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="89c1f-101">\<defaultPorts></span></span>
<span data-ttu-id="89c1f-102">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="89c1f-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="89c1f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="89c1f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="89c1f-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="89c1f-104">\<behaviors></span></span>  
<span data-ttu-id="89c1f-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="89c1f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="89c1f-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="89c1f-106">\<behavior></span></span>  
<span data-ttu-id="89c1f-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="89c1f-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="89c1f-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="89c1f-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c1f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="89c1f-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89c1f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89c1f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89c1f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89c1f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89c1f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89c1f-112">Attributes</span></span>  
 <span data-ttu-id="89c1f-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="89c1f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89c1f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89c1f-114">Child Elements</span></span>  
  
|<span data-ttu-id="89c1f-115">Element</span><span class="sxs-lookup"><span data-stu-id="89c1f-115">Element</span></span>|<span data-ttu-id="89c1f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="89c1f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89c1f-117">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="89c1f-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="89c1f-118">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="89c1f-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89c1f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89c1f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="89c1f-120">Element</span><span class="sxs-lookup"><span data-stu-id="89c1f-120">Element</span></span>|<span data-ttu-id="89c1f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="89c1f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89c1f-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="89c1f-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="89c1f-123">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="89c1f-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89c1f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89c1f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
