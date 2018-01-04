---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46fb4f1f4688aede484b177e30b8bc8dfff1ece2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="b95d6-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="b95d6-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="b95d6-103">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b95d6-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="b95d6-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b95d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b95d6-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b95d6-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95d6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b95d6-106">Syntax</span></span>  
  
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
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b95d6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b95d6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b95d6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b95d6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b95d6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b95d6-109">Attributes</span></span>  
 <span data-ttu-id="b95d6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="b95d6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b95d6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b95d6-111">Child Elements</span></span>  
  
|<span data-ttu-id="b95d6-112">Element</span><span class="sxs-lookup"><span data-stu-id="b95d6-112">Element</span></span>|<span data-ttu-id="b95d6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b95d6-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b95d6-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="b95d6-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="b95d6-115">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="b95d6-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b95d6-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b95d6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b95d6-117">Element</span><span class="sxs-lookup"><span data-stu-id="b95d6-117">Element</span></span>|<span data-ttu-id="b95d6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b95d6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b95d6-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b95d6-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b95d6-120">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="b95d6-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b95d6-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b95d6-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
