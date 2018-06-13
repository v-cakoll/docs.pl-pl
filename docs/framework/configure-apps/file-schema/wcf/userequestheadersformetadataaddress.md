---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766702"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="c2d7a-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="c2d7a-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="c2d7a-103">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c2d7a-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="c2d7a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c2d7a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c2d7a-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c2d7a-105">\<behaviors></span></span>  
<span data-ttu-id="c2d7a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c2d7a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c2d7a-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c2d7a-107">\<behavior></span></span>  
<span data-ttu-id="c2d7a-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="c2d7a-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d7a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2d7a-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2d7a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2d7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2d7a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2d7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2d7a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2d7a-112">Attributes</span></span>  
 <span data-ttu-id="c2d7a-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2d7a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2d7a-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2d7a-114">Child Elements</span></span>  
  
|<span data-ttu-id="c2d7a-115">Element</span><span class="sxs-lookup"><span data-stu-id="c2d7a-115">Element</span></span>|<span data-ttu-id="c2d7a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d7a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2d7a-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="c2d7a-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="c2d7a-118">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="c2d7a-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2d7a-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2d7a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c2d7a-120">Element</span><span class="sxs-lookup"><span data-stu-id="c2d7a-120">Element</span></span>|<span data-ttu-id="c2d7a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d7a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2d7a-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c2d7a-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c2d7a-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="c2d7a-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2d7a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2d7a-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
