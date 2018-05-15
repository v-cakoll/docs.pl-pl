---
title: '&lt;add&gt; w &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 159ab5a40a69c075b648a0c161babe604d13377b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="ab0db-102">&lt;add&gt; w &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="ab0db-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="ab0db-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ab0db-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="ab0db-104">Jeśli jest określony więcej niż jedną nazwę kontraktu, odpowie tylko punktów końcowych usługi dopasowania wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="ab0db-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="ab0db-105">Należy pamiętać, że w systemie Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ab0db-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="ab0db-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ab0db-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab0db-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ab0db-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0db-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab0db-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab0db-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab0db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab0db-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ab0db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab0db-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab0db-111">Attributes</span></span>  
  
|<span data-ttu-id="ab0db-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab0db-112">Attribute</span></span>|<span data-ttu-id="ab0db-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ab0db-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab0db-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="ab0db-114">name</span></span>|<span data-ttu-id="ab0db-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ab0db-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="ab0db-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ab0db-116">namespace</span></span>|<span data-ttu-id="ab0db-117">Ciąg określający obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ab0db-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab0db-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab0db-118">Child Elements</span></span>  
 <span data-ttu-id="ab0db-119">Brak</span><span class="sxs-lookup"><span data-stu-id="ab0db-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab0db-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab0db-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ab0db-121">Element</span><span class="sxs-lookup"><span data-stu-id="ab0db-121">Element</span></span>|<span data-ttu-id="ab0db-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ab0db-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab0db-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ab0db-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ab0db-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ab0db-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab0db-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab0db-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
