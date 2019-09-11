---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855413"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="8670f-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="8670f-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="8670f-102">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="8670f-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="8670f-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8670f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8670f-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8670f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8670f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="8670f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="8670f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="8670f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="8670f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="8670f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="8670f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClientSettings >**</span><span class="sxs-lookup"><span data-stu-id="8670f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8670f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8670f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8670f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8670f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8670f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8670f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8670f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8670f-112">Attributes</span></span>  
  
|<span data-ttu-id="8670f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8670f-113">Attribute</span></span>|<span data-ttu-id="8670f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8670f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8670f-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="8670f-115">discoveryEndpoint</span></span>|<span data-ttu-id="8670f-116">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8670f-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8670f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8670f-117">Child Elements</span></span>  
  
|<span data-ttu-id="8670f-118">Element</span><span class="sxs-lookup"><span data-stu-id="8670f-118">Element</span></span>|<span data-ttu-id="8670f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8670f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8670f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="8670f-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8670f-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8670f-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="8670f-122">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="8670f-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8670f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8670f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8670f-124">Element</span><span class="sxs-lookup"><span data-stu-id="8670f-124">Element</span></span>|<span data-ttu-id="8670f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8670f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8670f-126">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="8670f-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8670f-127">Definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8670f-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8670f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8670f-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
