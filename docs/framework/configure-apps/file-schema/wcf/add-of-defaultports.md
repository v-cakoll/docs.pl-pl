---
title: '&lt;add&gt; w &lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 8b7a4730af6690616058a91cf23bb39734d81abc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541719"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="d26a1-102">&lt;add&gt; w &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="d26a1-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="d26a1-103">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="d26a1-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="d26a1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d26a1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d26a1-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d26a1-105">\<behaviors></span></span>  
<span data-ttu-id="d26a1-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d26a1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d26a1-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d26a1-107">\<behavior></span></span>  
<span data-ttu-id="d26a1-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="d26a1-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="d26a1-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="d26a1-109">\<defaultPorts></span></span>  
<span data-ttu-id="d26a1-110">\<add></span><span class="sxs-lookup"><span data-stu-id="d26a1-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26a1-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="d26a1-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d26a1-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d26a1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d26a1-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d26a1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d26a1-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d26a1-114">Attributes</span></span>  
  
|<span data-ttu-id="d26a1-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d26a1-115">Attribute</span></span>|<span data-ttu-id="d26a1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d26a1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d26a1-117">port</span><span class="sxs-lookup"><span data-stu-id="d26a1-117">port</span></span>|<span data-ttu-id="d26a1-118">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="d26a1-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="d26a1-119">schemat</span><span class="sxs-lookup"><span data-stu-id="d26a1-119">scheme</span></span>|<span data-ttu-id="d26a1-120">Ciąg określający grupę ustawień protokołu skojarzonym z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="d26a1-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d26a1-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d26a1-121">Child Elements</span></span>  
 <span data-ttu-id="d26a1-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d26a1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d26a1-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d26a1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d26a1-124">Element</span><span class="sxs-lookup"><span data-stu-id="d26a1-124">Element</span></span>|<span data-ttu-id="d26a1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d26a1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d26a1-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="d26a1-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="d26a1-127">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="d26a1-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d26a1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d26a1-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
