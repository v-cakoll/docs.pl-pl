---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd2e9f3fd6d2cd0b99c6b63bc8ad0eefc9ff3e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="fa8be-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="fa8be-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="fa8be-103">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="fa8be-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="fa8be-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fa8be-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa8be-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fa8be-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa8be-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa8be-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" 
                        maxResults="Integer" 
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa8be-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa8be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fa8be-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa8be-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa8be-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa8be-109">Attributes</span></span>  
  
|<span data-ttu-id="fa8be-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fa8be-110">Attribute</span></span>|<span data-ttu-id="fa8be-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fa8be-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa8be-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="fa8be-112">discoveryEndpoint</span></span>|<span data-ttu-id="fa8be-113">Ciąg zawierający nazwę odnajdowania punktu końcowego, który umożliwia aplikacjom klienta automatycznie wyszukiwać wykrywalnej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa8be-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa8be-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa8be-114">Child Elements</span></span>  
  
|<span data-ttu-id="fa8be-115">Element</span><span class="sxs-lookup"><span data-stu-id="fa8be-115">Element</span></span>|<span data-ttu-id="fa8be-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fa8be-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa8be-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fa8be-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fa8be-118">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="fa8be-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="fa8be-119">Kryteria można grupować w kryteriów wyszukiwania (Określanie usług szukasz) i zakończenie odnalezienie (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="fa8be-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa8be-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa8be-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa8be-121">Element</span><span class="sxs-lookup"><span data-stu-id="fa8be-121">Element</span></span>|<span data-ttu-id="fa8be-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fa8be-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa8be-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fa8be-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fa8be-124">Definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa8be-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa8be-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa8be-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
