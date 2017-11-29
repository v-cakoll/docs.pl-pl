---
title: '&lt;add&gt; w &lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bebea15e6d1f24c95905355dbced33aa9c5150f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="34291-102">&lt;add&gt; w &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="34291-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="34291-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="34291-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="34291-104">Jeśli jest określony więcej niż jedną nazwę kontraktu, odpowie tylko punktów końcowych usługi dopasowania wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="34291-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="34291-105">Należy pamiętać, że w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], punkt końcowy może obsługiwać tylko jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="34291-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="34291-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="34291-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="34291-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="34291-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34291-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="34291-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34291-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34291-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34291-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34291-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34291-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34291-111">Attributes</span></span>  
  
|<span data-ttu-id="34291-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34291-112">Attribute</span></span>|<span data-ttu-id="34291-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34291-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34291-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="34291-114">name</span></span>|<span data-ttu-id="34291-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="34291-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="34291-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="34291-116">namespace</span></span>|<span data-ttu-id="34291-117">Ciąg określający obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="34291-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34291-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34291-118">Child Elements</span></span>  
 <span data-ttu-id="34291-119">Brak</span><span class="sxs-lookup"><span data-stu-id="34291-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34291-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34291-120">Parent Elements</span></span>  
  
|<span data-ttu-id="34291-121">Element</span><span class="sxs-lookup"><span data-stu-id="34291-121">Element</span></span>|<span data-ttu-id="34291-122">Opis</span><span class="sxs-lookup"><span data-stu-id="34291-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34291-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="34291-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="34291-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="34291-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34291-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34291-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
