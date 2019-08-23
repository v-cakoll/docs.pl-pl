---
title: <add> dla <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 24f1478b99aef909ae93f87a70be257e9ba10d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926750"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="70aad-102">\<Dodawanie > \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="70aad-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="70aad-103">Element konfiguracji, który określa nazwę kontraktu usług, których szukasz, i kryteria zwykle używane podczas wyszukiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="70aad-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="70aad-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowiedź będzie zawierać tylko punkty końcowe usługi pasujące do wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="70aad-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="70aad-105">Należy pamiętać, że w Windows Communication Foundation (WCF) punkt końcowy może obsługiwać tylko jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="70aad-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="70aad-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70aad-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="70aad-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="70aad-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70aad-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="70aad-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70aad-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70aad-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70aad-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70aad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70aad-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70aad-111">Attributes</span></span>  
  
|<span data-ttu-id="70aad-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="70aad-112">Attribute</span></span>|<span data-ttu-id="70aad-113">Opis</span><span class="sxs-lookup"><span data-stu-id="70aad-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70aad-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="70aad-114">name</span></span>|<span data-ttu-id="70aad-115">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="70aad-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="70aad-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="70aad-116">namespace</span></span>|<span data-ttu-id="70aad-117">Ciąg określający przestrzeń nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="70aad-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70aad-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70aad-118">Child Elements</span></span>  
 <span data-ttu-id="70aad-119">Brak</span><span class="sxs-lookup"><span data-stu-id="70aad-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70aad-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70aad-120">Parent Elements</span></span>  
  
|<span data-ttu-id="70aad-121">Element</span><span class="sxs-lookup"><span data-stu-id="70aad-121">Element</span></span>|<span data-ttu-id="70aad-122">Opis</span><span class="sxs-lookup"><span data-stu-id="70aad-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70aad-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="70aad-123">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="70aad-124">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="70aad-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70aad-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70aad-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
