---
title: <add> dla <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136750"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="39d5f-102">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="39d5f-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="39d5f-103">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="39d5f-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="39d5f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39d5f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39d5f-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="39d5f-105">\<behaviors></span></span>  
<span data-ttu-id="39d5f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="39d5f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="39d5f-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="39d5f-107">\<behavior></span></span>  
<span data-ttu-id="39d5f-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="39d5f-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="39d5f-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="39d5f-109">\<defaultPorts></span></span>  
<span data-ttu-id="39d5f-110">\<add></span><span class="sxs-lookup"><span data-stu-id="39d5f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d5f-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="39d5f-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39d5f-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39d5f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="39d5f-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39d5f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39d5f-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39d5f-114">Attributes</span></span>  
  
|<span data-ttu-id="39d5f-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39d5f-115">Attribute</span></span>|<span data-ttu-id="39d5f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="39d5f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39d5f-117">port</span><span class="sxs-lookup"><span data-stu-id="39d5f-117">port</span></span>|<span data-ttu-id="39d5f-118">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="39d5f-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="39d5f-119">schemat</span><span class="sxs-lookup"><span data-stu-id="39d5f-119">scheme</span></span>|<span data-ttu-id="39d5f-120">Ciąg określający grupę ustawień protokołu skojarzonym z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="39d5f-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39d5f-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39d5f-121">Child Elements</span></span>  
 <span data-ttu-id="39d5f-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="39d5f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39d5f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39d5f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="39d5f-124">Element</span><span class="sxs-lookup"><span data-stu-id="39d5f-124">Element</span></span>|<span data-ttu-id="39d5f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="39d5f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39d5f-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="39d5f-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="39d5f-127">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="39d5f-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39d5f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39d5f-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
