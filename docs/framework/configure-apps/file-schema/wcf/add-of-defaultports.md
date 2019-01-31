---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261607"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="5ff83-102">\<Dodaj > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="5ff83-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="5ff83-103">Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="5ff83-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="5ff83-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ff83-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ff83-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5ff83-105">\<behaviors></span></span>  
<span data-ttu-id="5ff83-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ff83-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5ff83-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5ff83-107">\<behavior></span></span>  
<span data-ttu-id="5ff83-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5ff83-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="5ff83-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5ff83-109">\<defaultPorts></span></span>  
<span data-ttu-id="5ff83-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5ff83-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff83-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ff83-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff83-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5ff83-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ff83-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5ff83-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff83-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ff83-114">Attributes</span></span>  
  
|<span data-ttu-id="5ff83-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ff83-115">Attribute</span></span>|<span data-ttu-id="5ff83-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5ff83-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ff83-117">port</span><span class="sxs-lookup"><span data-stu-id="5ff83-117">port</span></span>|<span data-ttu-id="5ff83-118">Liczba całkowita, która określa domyślny numer portu komunikacyjnego</span><span class="sxs-lookup"><span data-stu-id="5ff83-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="5ff83-119">schemat</span><span class="sxs-lookup"><span data-stu-id="5ff83-119">scheme</span></span>|<span data-ttu-id="5ff83-120">Ciąg określający grupę ustawień protokołu skojarzonym z portem komunikacyjnym.</span><span class="sxs-lookup"><span data-stu-id="5ff83-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ff83-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ff83-121">Child Elements</span></span>  
 <span data-ttu-id="5ff83-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5ff83-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff83-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5ff83-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff83-124">Element</span><span class="sxs-lookup"><span data-stu-id="5ff83-124">Element</span></span>|<span data-ttu-id="5ff83-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5ff83-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ff83-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5ff83-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="5ff83-127">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="5ff83-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ff83-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ff83-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
