---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940551"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="c4c6a-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="c4c6a-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="c4c6a-102">Umożliwia pobieranie informacji o adresie metadanych z nagłówków komunikatów żądania.</span><span class="sxs-lookup"><span data-stu-id="c4c6a-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="c4c6a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4c6a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4c6a-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="c4c6a-104">\<behaviors></span></span>  
<span data-ttu-id="c4c6a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4c6a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c4c6a-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c4c6a-106">\<behavior></span></span>  
<span data-ttu-id="c4c6a-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="c4c6a-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c6a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4c6a-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4c6a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c4c6a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c4c6a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c4c6a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4c6a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c4c6a-111">Attributes</span></span>  
 <span data-ttu-id="c4c6a-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c4c6a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4c6a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c4c6a-113">Child Elements</span></span>  
  
|<span data-ttu-id="c4c6a-114">Element</span><span class="sxs-lookup"><span data-stu-id="c4c6a-114">Element</span></span>|<span data-ttu-id="c4c6a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c4c6a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4c6a-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="c4c6a-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="c4c6a-117">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="c4c6a-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4c6a-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c4c6a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c4c6a-119">Element</span><span class="sxs-lookup"><span data-stu-id="c4c6a-119">Element</span></span>|<span data-ttu-id="c4c6a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c4c6a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4c6a-121">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c4c6a-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c4c6a-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="c4c6a-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4c6a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4c6a-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
