---
title: <add> dla <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850529"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="3c97b-102">\<Dodawanie > \<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="3c97b-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="3c97b-103">Element konfiguracji, który określa nazwę kontraktu usług, których szukasz, i kryteria zwykle używane podczas wyszukiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="3c97b-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="3c97b-104">Jeśli określono więcej niż jedną nazwę kontraktu, odpowiedź będzie zawierać tylko punkty końcowe usługi pasujące do wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="3c97b-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="3c97b-105">Należy pamiętać, że w Windows Communication Foundation (WCF) punkt końcowy może obsługiwać tylko jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="3c97b-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="3c97b-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3c97b-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3c97b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="3c97b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="3c97b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="3c97b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="3c97b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="3c97b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kryteria znajdowania >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="3c97b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<contractTypeNames >** ](contracttypenames.md)</span><span class="sxs-lookup"><span data-stu-id="3c97b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)</span></span>\
<span data-ttu-id="3c97b-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="3c97b-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c97b-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c97b-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c97b-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3c97b-116">Attributes and Elements</span></span>  
 <span data-ttu-id="3c97b-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3c97b-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c97b-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3c97b-118">Attributes</span></span>  
  
|<span data-ttu-id="3c97b-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3c97b-119">Attribute</span></span>|<span data-ttu-id="3c97b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3c97b-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c97b-121">nazwa</span><span class="sxs-lookup"><span data-stu-id="3c97b-121">name</span></span>|<span data-ttu-id="3c97b-122">Ciąg określający nazwę typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3c97b-122">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="3c97b-123">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3c97b-123">namespace</span></span>|<span data-ttu-id="3c97b-124">Ciąg określający przestrzeń nazw typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3c97b-124">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c97b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3c97b-125">Child Elements</span></span>  
 <span data-ttu-id="3c97b-126">Brak</span><span class="sxs-lookup"><span data-stu-id="3c97b-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c97b-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3c97b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3c97b-128">Element</span><span class="sxs-lookup"><span data-stu-id="3c97b-128">Element</span></span>|<span data-ttu-id="3c97b-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3c97b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c97b-130">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="3c97b-130">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="3c97b-131">Kolekcja nazw typów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3c97b-131">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c97b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c97b-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
