---
title: '&lt;add&gt; w &lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 28ddc98bd66c1f74f857448aa710d3998ddbd3dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="18fe0-102">&lt;add&gt; w &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="18fe0-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="18fe0-103">Domyślny punkt końcowy komunikacji, który aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="18fe0-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="18fe0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18fe0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18fe0-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="18fe0-105">\<behaviors></span></span>  
<span data-ttu-id="18fe0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="18fe0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="18fe0-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="18fe0-107">\<behavior></span></span>  
<span data-ttu-id="18fe0-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="18fe0-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="18fe0-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="18fe0-109">\<defaultPorts></span></span>  
<span data-ttu-id="18fe0-110">\<add></span><span class="sxs-lookup"><span data-stu-id="18fe0-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18fe0-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="18fe0-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18fe0-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18fe0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="18fe0-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18fe0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18fe0-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18fe0-114">Attributes</span></span>  
  
|<span data-ttu-id="18fe0-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="18fe0-115">Attribute</span></span>|<span data-ttu-id="18fe0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="18fe0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18fe0-117">port</span><span class="sxs-lookup"><span data-stu-id="18fe0-117">port</span></span>|<span data-ttu-id="18fe0-118">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="18fe0-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="18fe0-119">schemat</span><span class="sxs-lookup"><span data-stu-id="18fe0-119">scheme</span></span>|<span data-ttu-id="18fe0-120">Ciąg określający grupę ustawień protokołu skojarzonym z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="18fe0-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18fe0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18fe0-121">Child Elements</span></span>  
 <span data-ttu-id="18fe0-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="18fe0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18fe0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18fe0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="18fe0-124">Element</span><span class="sxs-lookup"><span data-stu-id="18fe0-124">Element</span></span>|<span data-ttu-id="18fe0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="18fe0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18fe0-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="18fe0-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="18fe0-127">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="18fe0-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18fe0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18fe0-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
