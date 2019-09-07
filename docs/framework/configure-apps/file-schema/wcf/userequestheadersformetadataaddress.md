---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399202"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="333ac-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="333ac-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="333ac-102">Umożliwia pobieranie informacji o adresie metadanych z nagłówków komunikatów żądania.</span><span class="sxs-lookup"><span data-stu-id="333ac-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="333ac-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="333ac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="333ac-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="333ac-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="333ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="333ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="333ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="333ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="333ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="333ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="333ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useRequestHeadersForMetadataAddress >**</span><span class="sxs-lookup"><span data-stu-id="333ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333ac-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="333ac-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="333ac-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="333ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="333ac-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="333ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="333ac-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="333ac-112">Attributes</span></span>  
 <span data-ttu-id="333ac-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="333ac-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="333ac-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="333ac-114">Child Elements</span></span>  
  
|<span data-ttu-id="333ac-115">Element</span><span class="sxs-lookup"><span data-stu-id="333ac-115">Element</span></span>|<span data-ttu-id="333ac-116">Opis</span><span class="sxs-lookup"><span data-stu-id="333ac-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="333ac-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="333ac-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="333ac-118">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="333ac-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="333ac-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="333ac-119">Parent Elements</span></span>  
  
|<span data-ttu-id="333ac-120">Element</span><span class="sxs-lookup"><span data-stu-id="333ac-120">Element</span></span>|<span data-ttu-id="333ac-121">Opis</span><span class="sxs-lookup"><span data-stu-id="333ac-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="333ac-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="333ac-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="333ac-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="333ac-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="333ac-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="333ac-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
