---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1886f6efdfaa8f4105e6ef16ad72093867e0f3fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="d7bd5-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="d7bd5-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="d7bd5-103">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="d7bd5-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="d7bd5-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7bd5-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-105">\<behaviors></span></span>  
<span data-ttu-id="d7bd5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d7bd5-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-107">\<behavior></span></span>  
<span data-ttu-id="d7bd5-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="d7bd5-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bd5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7bd5-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7bd5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d7bd5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d7bd5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d7bd5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7bd5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d7bd5-113">Attributes</span></span>  
 <span data-ttu-id="d7bd5-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d7bd5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7bd5-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d7bd5-115">Child Elements</span></span>  
  
|<span data-ttu-id="d7bd5-116">Element</span><span class="sxs-lookup"><span data-stu-id="d7bd5-116">Element</span></span>|<span data-ttu-id="d7bd5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d7bd5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7bd5-118">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="d7bd5-119">Domyślny punkt końcowy komunikacji, który aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="d7bd5-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7bd5-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d7bd5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d7bd5-121">Element</span><span class="sxs-lookup"><span data-stu-id="d7bd5-121">Element</span></span>|<span data-ttu-id="d7bd5-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d7bd5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7bd5-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="d7bd5-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="d7bd5-124">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="d7bd5-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7bd5-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7bd5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
