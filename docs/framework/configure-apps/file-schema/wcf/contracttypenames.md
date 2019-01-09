---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 60647e6ec31e7228f09d084ff669a1829770ca14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144734"
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="c262f-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="c262f-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="c262f-103">Sekcja konfiguracji, który określa listę nazw typu umowy, które są nazwy kontraktów usług wyszukane, i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c262f-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="c262f-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="c262f-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="c262f-105">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c262f-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="c262f-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c262f-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="c262f-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c262f-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c262f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c262f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c262f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c262f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c262f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c262f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c262f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c262f-111">Attributes</span></span>  
 <span data-ttu-id="c262f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c262f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c262f-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c262f-113">Child Elements</span></span>  
  
|<span data-ttu-id="c262f-114">Element</span><span class="sxs-lookup"><span data-stu-id="c262f-114">Element</span></span>|<span data-ttu-id="c262f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c262f-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c262f-116">\<add></span><span class="sxs-lookup"><span data-stu-id="c262f-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="c262f-117">Nazwa typu, który kontrakt jest właściwością, która odwołuje się do zestawu kryteriów zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c262f-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c262f-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c262f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c262f-119">Element</span><span class="sxs-lookup"><span data-stu-id="c262f-119">Element</span></span>|<span data-ttu-id="c262f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c262f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c262f-121">\<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="c262f-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="c262f-122">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="c262f-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c262f-123">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="c262f-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c262f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c262f-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
