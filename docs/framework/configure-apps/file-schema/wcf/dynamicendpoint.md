---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 78ec2d4639161f8e10105f205576f052c8a5567c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146839"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="5158d-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5158d-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="5158d-103">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5158d-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="5158d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5158d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5158d-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5158d-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5158d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5158d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5158d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5158d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5158d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5158d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5158d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5158d-109">Attributes</span></span>  
 <span data-ttu-id="5158d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="5158d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5158d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5158d-111">Child Elements</span></span>  
  
|<span data-ttu-id="5158d-112">Element</span><span class="sxs-lookup"><span data-stu-id="5158d-112">Element</span></span>|<span data-ttu-id="5158d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5158d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5158d-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="5158d-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="5158d-115">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="5158d-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5158d-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5158d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5158d-117">Element</span><span class="sxs-lookup"><span data-stu-id="5158d-117">Element</span></span>|<span data-ttu-id="5158d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5158d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5158d-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5158d-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5158d-120">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="5158d-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5158d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5158d-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
