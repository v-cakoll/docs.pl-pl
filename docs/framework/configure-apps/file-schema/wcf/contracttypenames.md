---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855454"
---
# <a name="contracttypenames"></a><span data-ttu-id="74cd7-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="74cd7-101">\<contractTypeNames></span></span>
<span data-ttu-id="74cd7-102">Sekcja konfiguracji określająca listę nazw typów kontraktów, które są nazwami kontraktów usług, których szukasz, oraz kryteriów zwykle używanych podczas wyszukiwania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="74cd7-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="74cd7-103">Jeśli określono więcej niż jedną nazwę kontraktu, odpowiedź będzie zawierać tylko punkty końcowe usługi pasujące do wszystkich umów.</span><span class="sxs-lookup"><span data-stu-id="74cd7-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="74cd7-104">Należy pamiętać, że w Windows Communication Foundation (WCF) punkt końcowy może obsługiwać tylko jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="74cd7-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="74cd7-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74cd7-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="74cd7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="74cd7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="74cd7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="74cd7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="74cd7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="74cd7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kryteria znajdowania >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="74cd7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="74cd7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<contractTypeNames >**</span><span class="sxs-lookup"><span data-stu-id="74cd7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74cd7-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="74cd7-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74cd7-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="74cd7-114">Attributes and Elements</span></span>  
 <span data-ttu-id="74cd7-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="74cd7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74cd7-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="74cd7-116">Attributes</span></span>  
 <span data-ttu-id="74cd7-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="74cd7-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74cd7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="74cd7-118">Child Elements</span></span>  
  
|<span data-ttu-id="74cd7-119">Element</span><span class="sxs-lookup"><span data-stu-id="74cd7-119">Element</span></span>|<span data-ttu-id="74cd7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="74cd7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74cd7-121">\<add></span><span class="sxs-lookup"><span data-stu-id="74cd7-121">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="74cd7-122">Nazwa typu kontraktu to właściwość, która odwołuje się do zestawu kryteriów zwykle używanych podczas wyszukiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="74cd7-122">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74cd7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="74cd7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="74cd7-124">Element</span><span class="sxs-lookup"><span data-stu-id="74cd7-124">Element</span></span>|<span data-ttu-id="74cd7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="74cd7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74cd7-126">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="74cd7-126">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="74cd7-127">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="74cd7-127">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="74cd7-128">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="74cd7-128">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74cd7-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74cd7-129">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
