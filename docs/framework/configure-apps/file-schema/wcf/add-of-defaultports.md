---
title: <add> dla <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926707"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="9f17d-102">\<Dodawanie > \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="9f17d-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="9f17d-103">Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="9f17d-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="9f17d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f17d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f17d-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="9f17d-105">\<behaviors></span></span>  
<span data-ttu-id="9f17d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f17d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f17d-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="9f17d-107">\<behavior></span></span>  
<span data-ttu-id="9f17d-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="9f17d-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="9f17d-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="9f17d-109">\<defaultPorts></span></span>  
<span data-ttu-id="9f17d-110">\<add></span><span class="sxs-lookup"><span data-stu-id="9f17d-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f17d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f17d-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f17d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f17d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9f17d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f17d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f17d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f17d-114">Attributes</span></span>  
  
|<span data-ttu-id="9f17d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9f17d-115">Attribute</span></span>|<span data-ttu-id="9f17d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9f17d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f17d-117">port</span><span class="sxs-lookup"><span data-stu-id="9f17d-117">port</span></span>|<span data-ttu-id="9f17d-118">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="9f17d-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="9f17d-119">schemat</span><span class="sxs-lookup"><span data-stu-id="9f17d-119">scheme</span></span>|<span data-ttu-id="9f17d-120">Ciąg określający grupę ustawień protokołu skojarzonych z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="9f17d-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f17d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f17d-121">Child Elements</span></span>  
 <span data-ttu-id="9f17d-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="9f17d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f17d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f17d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9f17d-124">Element</span><span class="sxs-lookup"><span data-stu-id="9f17d-124">Element</span></span>|<span data-ttu-id="9f17d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9f17d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f17d-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="9f17d-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="9f17d-127">Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="9f17d-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f17d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f17d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
