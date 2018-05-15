---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: e9723aed1aa8fbcbf5c4e84080c0ba991ea3fd60
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="f2a7f-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="f2a7f-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="f2a7f-103">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="f2a7f-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="f2a7f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f2a7f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2a7f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f2a7f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a7f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2a7f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2a7f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2a7f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f2a7f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f2a7f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2a7f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2a7f-109">Attributes</span></span>  
  
|<span data-ttu-id="f2a7f-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f2a7f-110">Attribute</span></span>|<span data-ttu-id="f2a7f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f2a7f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2a7f-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="f2a7f-112">discoveryEndpoint</span></span>|<span data-ttu-id="f2a7f-113">Ciąg zawierający nazwę odnajdowania punktu końcowego, który umożliwia aplikacjom klienta automatycznie wyszukiwać wykrywalnej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2a7f-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2a7f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2a7f-114">Child Elements</span></span>  
  
|<span data-ttu-id="f2a7f-115">Element</span><span class="sxs-lookup"><span data-stu-id="f2a7f-115">Element</span></span>|<span data-ttu-id="f2a7f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f2a7f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2a7f-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f2a7f-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f2a7f-118">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="f2a7f-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f2a7f-119">Kryteria można grupować w kryteriów wyszukiwania (Określanie usług szukasz) i zakończenie odnalezienie (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="f2a7f-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2a7f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2a7f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f2a7f-121">Element</span><span class="sxs-lookup"><span data-stu-id="f2a7f-121">Element</span></span>|<span data-ttu-id="f2a7f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f2a7f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2a7f-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f2a7f-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f2a7f-124">Definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2a7f-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2a7f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2a7f-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
