---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 0b014a9d797ded61949a374486824ee3ebc34661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673488"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="edde6-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="edde6-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="edde6-102">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="edde6-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="edde6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="edde6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="edde6-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="edde6-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edde6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="edde6-105">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edde6-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="edde6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="edde6-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="edde6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edde6-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="edde6-108">Attributes</span></span>  
  
|<span data-ttu-id="edde6-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="edde6-109">Attribute</span></span>|<span data-ttu-id="edde6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="edde6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edde6-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="edde6-111">discoveryEndpoint</span></span>|<span data-ttu-id="edde6-112">Ciąg, który zawiera nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienta automatycznie wyszukiwać odnajdywanej usługi i znaleźć jej adres w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="edde6-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edde6-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="edde6-113">Child Elements</span></span>  
  
|<span data-ttu-id="edde6-114">Element</span><span class="sxs-lookup"><span data-stu-id="edde6-114">Element</span></span>|<span data-ttu-id="edde6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="edde6-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edde6-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="edde6-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="edde6-117">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="edde6-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="edde6-118">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="edde6-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edde6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="edde6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="edde6-120">Element</span><span class="sxs-lookup"><span data-stu-id="edde6-120">Element</span></span>|<span data-ttu-id="edde6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="edde6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edde6-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="edde6-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="edde6-123">Definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="edde6-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edde6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edde6-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
