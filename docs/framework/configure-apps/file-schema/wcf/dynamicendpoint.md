---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 3dc7fb19c5c7729620a5d9f3df1111b2dbdacf78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925835"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="df98a-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="df98a-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="df98a-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="df98a-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="df98a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="df98a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="df98a-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="df98a-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df98a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="df98a-105">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df98a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="df98a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="df98a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="df98a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df98a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="df98a-108">Attributes</span></span>  
 <span data-ttu-id="df98a-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="df98a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df98a-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="df98a-110">Child Elements</span></span>  
  
|<span data-ttu-id="df98a-111">Element</span><span class="sxs-lookup"><span data-stu-id="df98a-111">Element</span></span>|<span data-ttu-id="df98a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="df98a-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df98a-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="df98a-113">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="df98a-114">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="df98a-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df98a-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="df98a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="df98a-116">Element</span><span class="sxs-lookup"><span data-stu-id="df98a-116">Element</span></span>|<span data-ttu-id="df98a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="df98a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df98a-118">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="df98a-118">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="df98a-119">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="df98a-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df98a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df98a-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
