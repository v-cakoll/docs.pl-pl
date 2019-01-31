---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 786a70e8c686497e91492938a4d0796db4f6dd91
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269799"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="9ef97-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="9ef97-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="9ef97-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9ef97-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="9ef97-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ef97-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ef97-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9ef97-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef97-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ef97-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ef97-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ef97-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9ef97-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ef97-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ef97-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ef97-108">Attributes</span></span>  
 <span data-ttu-id="9ef97-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ef97-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ef97-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ef97-110">Child Elements</span></span>  
  
|<span data-ttu-id="9ef97-111">Element</span><span class="sxs-lookup"><span data-stu-id="9ef97-111">Element</span></span>|<span data-ttu-id="9ef97-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9ef97-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ef97-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="9ef97-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="9ef97-114">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="9ef97-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ef97-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ef97-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9ef97-116">Element</span><span class="sxs-lookup"><span data-stu-id="9ef97-116">Element</span></span>|<span data-ttu-id="9ef97-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9ef97-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ef97-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9ef97-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9ef97-119">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="9ef97-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ef97-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ef97-120">See also</span></span>
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
