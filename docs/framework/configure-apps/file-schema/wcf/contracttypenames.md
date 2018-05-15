---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 99547967b65e5d7663ec11be98247e2018aaa34c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="9573b-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="9573b-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="9573b-103">Sekcja konfiguracyjna, który określa listę nazw typ kontraktu, które są nazwy kontraktu usługi wyszukane, i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9573b-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="9573b-104">Jeśli jest określony więcej niż jedną nazwę kontraktu, odpowie tylko punktów końcowych usługi dopasowania wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="9573b-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="9573b-105">Należy pamiętać, że w systemie Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9573b-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="9573b-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9573b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="9573b-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9573b-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9573b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9573b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9573b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9573b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9573b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9573b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9573b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9573b-111">Attributes</span></span>  
 <span data-ttu-id="9573b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="9573b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9573b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9573b-113">Child Elements</span></span>  
  
|<span data-ttu-id="9573b-114">Element</span><span class="sxs-lookup"><span data-stu-id="9573b-114">Element</span></span>|<span data-ttu-id="9573b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9573b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9573b-116">\<add></span><span class="sxs-lookup"><span data-stu-id="9573b-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="9573b-117">Właściwość, która odwołuje się do zestawu kryteriów zwykle używana podczas wyszukiwania dla usługi jest nazwa typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9573b-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9573b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9573b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9573b-119">Element</span><span class="sxs-lookup"><span data-stu-id="9573b-119">Element</span></span>|<span data-ttu-id="9573b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9573b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9573b-121">\<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="9573b-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="9573b-122">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="9573b-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9573b-123">Kryteria można grupować w kryteriów wyszukiwania (Określanie usług szukasz) i zakończenie odnalezienie (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="9573b-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9573b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9573b-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
