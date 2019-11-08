---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739035"
---
# <a name="discoveryclient"></a><span data-ttu-id="c8388-101">\<obiekt DiscoveryClient ></span><span class="sxs-lookup"><span data-stu-id="c8388-101">\<discoveryClient></span></span>
<span data-ttu-id="c8388-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c8388-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="c8388-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c8388-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c8388-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c8388-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c8388-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="c8388-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c8388-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="c8388-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="c8388-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="c8388-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c8388-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<obiekt discoveryclient >**</span><span class="sxs-lookup"><span data-stu-id="c8388-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8388-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8388-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8388-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8388-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c8388-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8388-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8388-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8388-112">Attributes</span></span>  
  
|<span data-ttu-id="c8388-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8388-113">Attribute</span></span>|<span data-ttu-id="c8388-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c8388-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8388-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="c8388-115">discoveryEndpoint</span></span>|<span data-ttu-id="c8388-116">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c8388-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8388-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8388-117">Child Elements</span></span>  
  
|<span data-ttu-id="c8388-118">Element</span><span class="sxs-lookup"><span data-stu-id="c8388-118">Element</span></span>|<span data-ttu-id="c8388-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c8388-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8388-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c8388-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c8388-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c8388-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c8388-122">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="c8388-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8388-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8388-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c8388-124">Element</span><span class="sxs-lookup"><span data-stu-id="c8388-124">Element</span></span>|<span data-ttu-id="c8388-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c8388-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8388-126">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="c8388-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="c8388-127">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8388-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8388-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8388-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
