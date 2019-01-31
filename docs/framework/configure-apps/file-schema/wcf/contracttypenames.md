---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: d8f2b600b700a19cf587a6c8c4cc3f0e851edbd9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261286"
---
# <a name="contracttypenames"></a><span data-ttu-id="84a7c-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="84a7c-101">\<contractTypeNames></span></span>
<span data-ttu-id="84a7c-102">Sekcja konfiguracji, który określa listę nazw typu umowy, które są nazwy kontraktów usług wyszukane, i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="84a7c-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="84a7c-103">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="84a7c-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="84a7c-104">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="84a7c-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="84a7c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84a7c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="84a7c-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="84a7c-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a7c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="84a7c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84a7c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="84a7c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="84a7c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="84a7c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84a7c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="84a7c-110">Attributes</span></span>  
 <span data-ttu-id="84a7c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="84a7c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84a7c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="84a7c-112">Child Elements</span></span>  
  
|<span data-ttu-id="84a7c-113">Element</span><span class="sxs-lookup"><span data-stu-id="84a7c-113">Element</span></span>|<span data-ttu-id="84a7c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="84a7c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84a7c-115">\<add></span><span class="sxs-lookup"><span data-stu-id="84a7c-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="84a7c-116">Nazwa typu, który kontrakt jest właściwością, która odwołuje się do zestawu kryteriów zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="84a7c-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84a7c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="84a7c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="84a7c-118">Element</span><span class="sxs-lookup"><span data-stu-id="84a7c-118">Element</span></span>|<span data-ttu-id="84a7c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="84a7c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84a7c-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="84a7c-120">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="84a7c-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="84a7c-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="84a7c-122">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="84a7c-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84a7c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84a7c-123">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
