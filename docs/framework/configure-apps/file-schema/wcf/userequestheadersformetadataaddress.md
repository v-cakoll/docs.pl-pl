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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="183ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="183ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="183ce-103">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="183ce-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="183ce-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="183ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="183ce-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="183ce-105">\<behaviors></span></span>  
<span data-ttu-id="183ce-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="183ce-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="183ce-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="183ce-107">\<behavior></span></span>  
<span data-ttu-id="183ce-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="183ce-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183ce-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="183ce-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="183ce-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="183ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="183ce-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="183ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="183ce-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="183ce-112">Attributes</span></span>  
 <span data-ttu-id="183ce-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="183ce-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="183ce-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="183ce-114">Child Elements</span></span>  
  
|<span data-ttu-id="183ce-115">Element</span><span class="sxs-lookup"><span data-stu-id="183ce-115">Element</span></span>|<span data-ttu-id="183ce-116">Opis</span><span class="sxs-lookup"><span data-stu-id="183ce-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="183ce-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="183ce-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="183ce-118">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="183ce-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="183ce-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="183ce-119">Parent Elements</span></span>  
  
|<span data-ttu-id="183ce-120">Element</span><span class="sxs-lookup"><span data-stu-id="183ce-120">Element</span></span>|<span data-ttu-id="183ce-121">Opis</span><span class="sxs-lookup"><span data-stu-id="183ce-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="183ce-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="183ce-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="183ce-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="183ce-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="183ce-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="183ce-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
