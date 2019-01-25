---
title: '&lt;add&gt; w &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: cf9a1ae28b53b841ac5d8d85d31e1548e36369ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735730"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="f7787-102">&lt;add&gt; w &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="f7787-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="f7787-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f7787-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="f7787-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="f7787-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="f7787-105">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7787-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="f7787-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f7787-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7787-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="f7787-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7787-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7787-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7787-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f7787-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f7787-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f7787-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7787-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f7787-111">Attributes</span></span>  
  
|<span data-ttu-id="f7787-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f7787-112">Attribute</span></span>|<span data-ttu-id="f7787-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f7787-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7787-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="f7787-114">name</span></span>|<span data-ttu-id="f7787-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7787-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="f7787-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f7787-116">namespace</span></span>|<span data-ttu-id="f7787-117">Ciąg, który określa obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7787-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7787-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f7787-118">Child Elements</span></span>  
 <span data-ttu-id="f7787-119">Brak</span><span class="sxs-lookup"><span data-stu-id="f7787-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7787-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f7787-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f7787-121">Element</span><span class="sxs-lookup"><span data-stu-id="f7787-121">Element</span></span>|<span data-ttu-id="f7787-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f7787-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7787-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="f7787-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="f7787-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f7787-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f7787-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7787-125">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
