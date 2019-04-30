---
title: <add> dla <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701193"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="669b9-102">\<Dodaj > z \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="669b9-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="669b9-103">Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="669b9-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="669b9-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="669b9-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="669b9-105">Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="669b9-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="669b9-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="669b9-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="669b9-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="669b9-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669b9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="669b9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="669b9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="669b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="669b9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="669b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="669b9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="669b9-111">Attributes</span></span>  
  
|<span data-ttu-id="669b9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="669b9-112">Attribute</span></span>|<span data-ttu-id="669b9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="669b9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="669b9-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="669b9-114">name</span></span>|<span data-ttu-id="669b9-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="669b9-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="669b9-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="669b9-116">namespace</span></span>|<span data-ttu-id="669b9-117">Ciąg, który określa obszar nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="669b9-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="669b9-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="669b9-118">Child Elements</span></span>  
 <span data-ttu-id="669b9-119">Brak</span><span class="sxs-lookup"><span data-stu-id="669b9-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="669b9-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="669b9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="669b9-121">Element</span><span class="sxs-lookup"><span data-stu-id="669b9-121">Element</span></span>|<span data-ttu-id="669b9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="669b9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="669b9-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="669b9-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="669b9-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="669b9-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="669b9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="669b9-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
