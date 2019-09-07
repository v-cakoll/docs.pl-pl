---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400403"
---
# <a name="discoveryclient"></a><span data-ttu-id="1a910-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="1a910-101">\<discoveryClient></span></span>
<span data-ttu-id="1a910-102">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a910-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="1a910-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1a910-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1a910-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1a910-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1a910-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1a910-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1a910-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="1a910-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="1a910-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="1a910-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1a910-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Obiekt DiscoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="1a910-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a910-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a910-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a910-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a910-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a910-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a910-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a910-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a910-112">Attributes</span></span>  
  
|<span data-ttu-id="1a910-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a910-113">Attribute</span></span>|<span data-ttu-id="1a910-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1a910-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a910-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="1a910-115">discoveryEndpoint</span></span>|<span data-ttu-id="1a910-116">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a910-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a910-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a910-117">Child Elements</span></span>  
  
|<span data-ttu-id="1a910-118">Element</span><span class="sxs-lookup"><span data-stu-id="1a910-118">Element</span></span>|<span data-ttu-id="1a910-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1a910-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a910-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1a910-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1a910-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1a910-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1a910-122">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="1a910-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a910-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a910-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1a910-124">Element</span><span class="sxs-lookup"><span data-stu-id="1a910-124">Element</span></span>|<span data-ttu-id="1a910-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1a910-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a910-126">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="1a910-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1a910-127">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1a910-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a910-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a910-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
