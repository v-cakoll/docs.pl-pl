---
title: <add> dla <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400641"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="68b70-102">\<Dodawanie > \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="68b70-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="68b70-103">Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="68b70-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="68b70-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="68b70-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="68b70-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="68b70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="68b70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="68b70-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="68b70-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultPorts >** ](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="68b70-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="68b70-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="68b70-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b70-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="68b70-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68b70-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="68b70-113">Attributes and Elements</span></span>  
 <span data-ttu-id="68b70-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="68b70-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b70-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="68b70-115">Attributes</span></span>  
  
|<span data-ttu-id="68b70-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="68b70-116">Attribute</span></span>|<span data-ttu-id="68b70-117">Opis</span><span class="sxs-lookup"><span data-stu-id="68b70-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68b70-118">port</span><span class="sxs-lookup"><span data-stu-id="68b70-118">port</span></span>|<span data-ttu-id="68b70-119">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="68b70-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="68b70-120">schemat</span><span class="sxs-lookup"><span data-stu-id="68b70-120">scheme</span></span>|<span data-ttu-id="68b70-121">Ciąg określający grupę ustawień protokołu skojarzonych z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="68b70-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68b70-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="68b70-122">Child Elements</span></span>  
 <span data-ttu-id="68b70-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="68b70-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68b70-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="68b70-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68b70-125">Element</span><span class="sxs-lookup"><span data-stu-id="68b70-125">Element</span></span>|<span data-ttu-id="68b70-126">Opis</span><span class="sxs-lookup"><span data-stu-id="68b70-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68b70-127">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="68b70-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="68b70-128">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="68b70-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68b70-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68b70-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
