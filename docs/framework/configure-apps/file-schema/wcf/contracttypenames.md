---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 12f9d4eca02ae3b306646826667c4eafef51a95c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919378"
---
# <a name="contracttypenames"></a><span data-ttu-id="fca44-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="fca44-101">\<contractTypeNames></span></span>
<span data-ttu-id="fca44-102">Sekcja konfiguracji określająca listę nazw typów kontraktów, które są nazwami kontraktów usług, których szukasz, oraz kryteriów zwykle używanych podczas wyszukiwania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="fca44-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="fca44-103">Jeśli określono więcej niż jedną nazwę kontraktu, odpowiedź będzie zawierać tylko punkty końcowe usługi pasujące do wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="fca44-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="fca44-104">Należy pamiętać, że w Windows Communication Foundation (WCF) punkt końcowy może obsługiwać tylko jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="fca44-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="fca44-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fca44-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fca44-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="fca44-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca44-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fca44-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fca44-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fca44-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fca44-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fca44-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fca44-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fca44-110">Attributes</span></span>  
 <span data-ttu-id="fca44-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="fca44-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fca44-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fca44-112">Child Elements</span></span>  
  
|<span data-ttu-id="fca44-113">Element</span><span class="sxs-lookup"><span data-stu-id="fca44-113">Element</span></span>|<span data-ttu-id="fca44-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fca44-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fca44-115">\<add></span><span class="sxs-lookup"><span data-stu-id="fca44-115">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="fca44-116">Nazwa typu kontraktu to właściwość, która odwołuje się do zestawu kryteriów zwykle używanych podczas wyszukiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="fca44-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fca44-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fca44-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fca44-118">Element</span><span class="sxs-lookup"><span data-stu-id="fca44-118">Element</span></span>|<span data-ttu-id="fca44-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fca44-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fca44-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="fca44-120">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="fca44-121">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="fca44-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="fca44-122">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="fca44-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fca44-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fca44-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
