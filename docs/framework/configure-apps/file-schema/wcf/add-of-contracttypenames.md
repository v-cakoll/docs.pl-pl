---
title: '&lt;add&gt; w &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 79972eaea6918b3fe923c963b6a219fd8f972516
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145617"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="ed0e4-102">&lt;add&gt; w &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="ed0e4-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="ed0e4-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="ed0e4-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="ed0e4-105">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="ed0e4-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed0e4-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed0e4-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ed0e4-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed0e4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed0e4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed0e4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ed0e4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ed0e4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed0e4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ed0e4-111">Attributes</span></span>  
  
|<span data-ttu-id="ed0e4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ed0e4-112">Attribute</span></span>|<span data-ttu-id="ed0e4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ed0e4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed0e4-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="ed0e4-114">name</span></span>|<span data-ttu-id="ed0e4-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="ed0e4-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ed0e4-116">namespace</span></span>|<span data-ttu-id="ed0e4-117">Ciąg, który określa obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed0e4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed0e4-118">Child Elements</span></span>  
 <span data-ttu-id="ed0e4-119">Brak</span><span class="sxs-lookup"><span data-stu-id="ed0e4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed0e4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ed0e4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ed0e4-121">Element</span><span class="sxs-lookup"><span data-stu-id="ed0e4-121">Element</span></span>|<span data-ttu-id="ed0e4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ed0e4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed0e4-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ed0e4-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ed0e4-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed0e4-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed0e4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed0e4-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
