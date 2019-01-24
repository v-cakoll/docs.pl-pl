---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 6c03057fca23b037702c702b9a574045ebb302b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656638"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="b16d2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="b16d2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="b16d2-103">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b16d2-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b16d2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b16d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b16d2-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b16d2-105">\<behaviors></span></span>  
<span data-ttu-id="b16d2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b16d2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b16d2-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b16d2-107">\<behavior></span></span>  
<span data-ttu-id="b16d2-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b16d2-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b16d2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b16d2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b16d2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b16d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b16d2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b16d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b16d2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b16d2-112">Attributes</span></span>  
 <span data-ttu-id="b16d2-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="b16d2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b16d2-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b16d2-114">Child Elements</span></span>  
  
|<span data-ttu-id="b16d2-115">Element</span><span class="sxs-lookup"><span data-stu-id="b16d2-115">Element</span></span>|<span data-ttu-id="b16d2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b16d2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b16d2-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b16d2-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="b16d2-118">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="b16d2-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b16d2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b16d2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b16d2-120">Element</span><span class="sxs-lookup"><span data-stu-id="b16d2-120">Element</span></span>|<span data-ttu-id="b16d2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b16d2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b16d2-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b16d2-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b16d2-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="b16d2-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b16d2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b16d2-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
