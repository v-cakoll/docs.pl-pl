---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925891"
---
# <a name="defaultports"></a><span data-ttu-id="ce78b-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ce78b-101">\<defaultPorts></span></span>
<span data-ttu-id="ce78b-102">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="ce78b-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="ce78b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ce78b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce78b-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="ce78b-104">\<behaviors></span></span>  
<span data-ttu-id="ce78b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ce78b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ce78b-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ce78b-106">\<behavior></span></span>  
<span data-ttu-id="ce78b-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="ce78b-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="ce78b-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ce78b-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce78b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce78b-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce78b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce78b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ce78b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce78b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce78b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce78b-112">Attributes</span></span>  
 <span data-ttu-id="ce78b-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce78b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ce78b-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce78b-114">Child Elements</span></span>  
  
|<span data-ttu-id="ce78b-115">Element</span><span class="sxs-lookup"><span data-stu-id="ce78b-115">Element</span></span>|<span data-ttu-id="ce78b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ce78b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce78b-117">\<Dodawanie > \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ce78b-117">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="ce78b-118">Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="ce78b-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce78b-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce78b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ce78b-120">Element</span><span class="sxs-lookup"><span data-stu-id="ce78b-120">Element</span></span>|<span data-ttu-id="ce78b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ce78b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce78b-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="ce78b-122">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="ce78b-123">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="ce78b-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce78b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce78b-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
