---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925863"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="c458a-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="c458a-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="c458a-102">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="c458a-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="c458a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c458a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c458a-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c458a-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c458a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c458a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c458a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c458a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c458a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c458a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c458a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c458a-108">Attributes</span></span>  
  
|<span data-ttu-id="c458a-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c458a-109">Attribute</span></span>|<span data-ttu-id="c458a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c458a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c458a-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="c458a-111">discoveryEndpoint</span></span>|<span data-ttu-id="c458a-112">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c458a-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c458a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c458a-113">Child Elements</span></span>  
  
|<span data-ttu-id="c458a-114">Element</span><span class="sxs-lookup"><span data-stu-id="c458a-114">Element</span></span>|<span data-ttu-id="c458a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c458a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c458a-116">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c458a-116">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c458a-117">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="c458a-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c458a-118">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="c458a-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c458a-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c458a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c458a-120">Element</span><span class="sxs-lookup"><span data-stu-id="c458a-120">Element</span></span>|<span data-ttu-id="c458a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c458a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c458a-122">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c458a-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c458a-123">Definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c458a-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c458a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c458a-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
