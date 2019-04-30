---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704118"
---
# <a name="defaultports"></a><span data-ttu-id="fad21-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="fad21-101">\<defaultPorts></span></span>
<span data-ttu-id="fad21-102">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="fad21-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="fad21-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fad21-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fad21-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="fad21-104">\<behaviors></span></span>  
<span data-ttu-id="fad21-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fad21-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="fad21-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fad21-106">\<behavior></span></span>  
<span data-ttu-id="fad21-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="fad21-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="fad21-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="fad21-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fad21-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fad21-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fad21-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fad21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fad21-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fad21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fad21-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fad21-112">Attributes</span></span>  
 <span data-ttu-id="fad21-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="fad21-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fad21-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fad21-114">Child Elements</span></span>  
  
|<span data-ttu-id="fad21-115">Element</span><span class="sxs-lookup"><span data-stu-id="fad21-115">Element</span></span>|<span data-ttu-id="fad21-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fad21-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fad21-117">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="fad21-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="fad21-118">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="fad21-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fad21-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fad21-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fad21-120">Element</span><span class="sxs-lookup"><span data-stu-id="fad21-120">Element</span></span>|<span data-ttu-id="fad21-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fad21-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fad21-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="fad21-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="fad21-123">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="fad21-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fad21-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fad21-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
