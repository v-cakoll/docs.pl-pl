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
ms.openlocfilehash: 1e7f69da871376f83422fb330f8babd56bb1fdcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="40bad-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="40bad-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="40bad-103">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="40bad-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="40bad-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40bad-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40bad-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="40bad-105">\<behaviors></span></span>  
<span data-ttu-id="40bad-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40bad-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="40bad-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="40bad-107">\<behavior></span></span>  
<span data-ttu-id="40bad-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="40bad-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40bad-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="40bad-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40bad-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="40bad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40bad-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="40bad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40bad-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="40bad-112">Attributes</span></span>  
 <span data-ttu-id="40bad-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="40bad-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40bad-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="40bad-114">Child Elements</span></span>  
  
|<span data-ttu-id="40bad-115">Element</span><span class="sxs-lookup"><span data-stu-id="40bad-115">Element</span></span>|<span data-ttu-id="40bad-116">Opis</span><span class="sxs-lookup"><span data-stu-id="40bad-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40bad-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="40bad-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="40bad-118">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="40bad-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40bad-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="40bad-119">Parent Elements</span></span>  
  
|<span data-ttu-id="40bad-120">Element</span><span class="sxs-lookup"><span data-stu-id="40bad-120">Element</span></span>|<span data-ttu-id="40bad-121">Opis</span><span class="sxs-lookup"><span data-stu-id="40bad-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40bad-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="40bad-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="40bad-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="40bad-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40bad-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40bad-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
