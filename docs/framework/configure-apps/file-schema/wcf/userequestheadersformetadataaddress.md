---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94dafcfa68463a0e82696cf16a96abe45632e72a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="24d3d-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="24d3d-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="24d3d-103">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="24d3d-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="24d3d-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="24d3d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24d3d-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="24d3d-105">\<behaviors></span></span>  
<span data-ttu-id="24d3d-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="24d3d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="24d3d-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="24d3d-107">\<behavior></span></span>  
<span data-ttu-id="24d3d-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="24d3d-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d3d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="24d3d-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24d3d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24d3d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24d3d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24d3d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24d3d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24d3d-112">Attributes</span></span>  
 <span data-ttu-id="24d3d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="24d3d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24d3d-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24d3d-114">Child Elements</span></span>  
  
|<span data-ttu-id="24d3d-115">Element</span><span class="sxs-lookup"><span data-stu-id="24d3d-115">Element</span></span>|<span data-ttu-id="24d3d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="24d3d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24d3d-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="24d3d-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="24d3d-118">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="24d3d-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24d3d-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24d3d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="24d3d-120">Element</span><span class="sxs-lookup"><span data-stu-id="24d3d-120">Element</span></span>|<span data-ttu-id="24d3d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="24d3d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24d3d-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="24d3d-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="24d3d-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="24d3d-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24d3d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24d3d-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
