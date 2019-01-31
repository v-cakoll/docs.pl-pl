---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: fa67d2ec21494bb3d84861f4c2e2e39151aac28f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253722"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="e3fff-102">\<Dodaj > z \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="e3fff-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="e3fff-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="e3fff-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="e3fff-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="e3fff-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="e3fff-105">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e3fff-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="e3fff-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3fff-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3fff-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e3fff-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3fff-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3fff-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3fff-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3fff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3fff-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3fff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3fff-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3fff-111">Attributes</span></span>  
  
|<span data-ttu-id="e3fff-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e3fff-112">Attribute</span></span>|<span data-ttu-id="e3fff-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e3fff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3fff-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="e3fff-114">name</span></span>|<span data-ttu-id="e3fff-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e3fff-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="e3fff-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e3fff-116">namespace</span></span>|<span data-ttu-id="e3fff-117">Ciąg, który określa obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e3fff-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3fff-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3fff-118">Child Elements</span></span>  
 <span data-ttu-id="e3fff-119">Brak</span><span class="sxs-lookup"><span data-stu-id="e3fff-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3fff-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3fff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e3fff-121">Element</span><span class="sxs-lookup"><span data-stu-id="e3fff-121">Element</span></span>|<span data-ttu-id="e3fff-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e3fff-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3fff-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="e3fff-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="e3fff-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e3fff-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3fff-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3fff-125">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
