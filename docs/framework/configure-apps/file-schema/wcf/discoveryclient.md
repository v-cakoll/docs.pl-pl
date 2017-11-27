---
title: '&lt;Obiekt discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0b7161c9e4564367348d1c94d469d6fa4a4b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="e77c0-102">&lt;Obiekt discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="e77c0-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="e77c0-103">Element konfiguracji do tworzenia niestandardowego powiązania, który umożliwia aplikacjom klienta automatycznie wyszukiwać wykrywalnej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e77c0-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="e77c0-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e77c0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e77c0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e77c0-105">\<bindings></span></span>  
<span data-ttu-id="e77c0-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e77c0-106">\<customBinding></span></span>  
<span data-ttu-id="e77c0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e77c0-107">\<binding></span></span>  
<span data-ttu-id="e77c0-108">\<Obiekt discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="e77c0-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e77c0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e77c0-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e77c0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e77c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e77c0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e77c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e77c0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e77c0-112">Attributes</span></span>  
  
|<span data-ttu-id="e77c0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e77c0-113">Attribute</span></span>|<span data-ttu-id="e77c0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e77c0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e77c0-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="e77c0-115">discoveryEndpoint</span></span>|<span data-ttu-id="e77c0-116">Ciąg zawierający nazwę odnajdowania punktu końcowego, który umożliwia aplikacjom klienta automatycznie wyszukiwać wykrywalnej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e77c0-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e77c0-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e77c0-117">Child Elements</span></span>  
  
|<span data-ttu-id="e77c0-118">Element</span><span class="sxs-lookup"><span data-stu-id="e77c0-118">Element</span></span>|<span data-ttu-id="e77c0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e77c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e77c0-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e77c0-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e77c0-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="e77c0-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="e77c0-122">Kryteria można grupować w kryteriów wyszukiwania (Określanie usług szukasz) i zakończenie odnalezienie (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="e77c0-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e77c0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e77c0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e77c0-124">Element</span><span class="sxs-lookup"><span data-stu-id="e77c0-124">Element</span></span>|<span data-ttu-id="e77c0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e77c0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e77c0-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e77c0-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e77c0-127">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e77c0-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e77c0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e77c0-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
