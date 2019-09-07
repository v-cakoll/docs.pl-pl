---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398071"
---
# <a name="defaultports"></a><span data-ttu-id="ca38c-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ca38c-101">\<defaultPorts></span></span>
<span data-ttu-id="ca38c-102">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="ca38c-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="ca38c-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca38c-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ca38c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ca38c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ca38c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ca38c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="ca38c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="ca38c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultPorts >**</span><span class="sxs-lookup"><span data-stu-id="ca38c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca38c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca38c-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca38c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca38c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca38c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca38c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca38c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca38c-113">Attributes</span></span>  
 <span data-ttu-id="ca38c-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca38c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca38c-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca38c-115">Child Elements</span></span>  
  
|<span data-ttu-id="ca38c-116">Element</span><span class="sxs-lookup"><span data-stu-id="ca38c-116">Element</span></span>|<span data-ttu-id="ca38c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ca38c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca38c-118">\<Dodawanie > \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ca38c-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="ca38c-119">Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="ca38c-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca38c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca38c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ca38c-121">Element</span><span class="sxs-lookup"><span data-stu-id="ca38c-121">Element</span></span>|<span data-ttu-id="ca38c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ca38c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca38c-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="ca38c-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="ca38c-124">Lista domyślnych portów.</span><span class="sxs-lookup"><span data-stu-id="ca38c-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca38c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca38c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
