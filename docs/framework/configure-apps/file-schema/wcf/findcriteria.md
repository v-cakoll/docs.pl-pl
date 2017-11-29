---
title: '&lt;kryteria znajdowania&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b428d1a95ec6f1f493c831f66223f52e4723990c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="6aced-102">&lt;kryteria znajdowania&gt;</span><span class="sxs-lookup"><span data-stu-id="6aced-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="6aced-103">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="6aced-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6aced-104">Kryteria można grupować w kryteriów wyszukiwania (Określanie usług szukasz) i zakończenie odnalezienie (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="6aced-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="6aced-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6aced-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6aced-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="6aced-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aced-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6aced-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aced-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6aced-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6aced-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6aced-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aced-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6aced-110">Attributes</span></span>  
  
|<span data-ttu-id="6aced-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6aced-111">Attribute</span></span>|<span data-ttu-id="6aced-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6aced-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6aced-113">czas trwania</span><span class="sxs-lookup"><span data-stu-id="6aced-113">duration</span></span>|<span data-ttu-id="6aced-114">Wartość Timespan określa maksymalny czas oczekiwania na odpowiedzi z usług w sieci.</span><span class="sxs-lookup"><span data-stu-id="6aced-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="6aced-115">Czas domyślny to 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="6aced-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="6aced-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="6aced-116">maxResults</span></span>|<span data-ttu-id="6aced-117">Liczba całkowita określająca maksymalną liczbę odpowiedzi zaczekać z usług w sieci lub Internetu.</span><span class="sxs-lookup"><span data-stu-id="6aced-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="6aced-118">Jeśli maksymalny odpowiedzi są odbierane przed wartością określoną w `duration` atrybutu upłynął zakończenia operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="6aced-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="6aced-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="6aced-119">scopeMatchBy</span></span>|<span data-ttu-id="6aced-120">Identyfikator URI, który określa algorytm dopasowania do użycia podczas dopasowywania zakresów w wiadomości sondy z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="6aced-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="6aced-121">Istnieją pięć obsługiwane reguły dopasowywania zakresu.</span><span class="sxs-lookup"><span data-stu-id="6aced-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="6aced-122">Jeśli nie określisz regułę dopasowania zakresu `ScopeMatchByPrefix` jest używany.</span><span class="sxs-lookup"><span data-stu-id="6aced-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="6aced-123">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="6aced-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6aced-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6aced-124">Child Elements</span></span>  
  
|<span data-ttu-id="6aced-125">Element</span><span class="sxs-lookup"><span data-stu-id="6aced-125">Element</span></span>|<span data-ttu-id="6aced-126">Opis</span><span class="sxs-lookup"><span data-stu-id="6aced-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aced-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="6aced-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="6aced-128">Kolekcja elementów konfiguracji, które zawierają nazwy typów kontraktu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6aced-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="6aced-129">\<Rozszerzenia > z \<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="6aced-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="6aced-130">Kolekcja obiektów — element XML, które udostępniają rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6aced-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="6aced-131">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="6aced-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="6aced-132">Kolekcja obiektów zawierających bezwzględny identyfikator URI, które są używane podczas operacji wyszukiwania można znaleźć określonej usługi lub usług.</span><span class="sxs-lookup"><span data-stu-id="6aced-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="6aced-133">Jeśli zostanie znaleziony określonej usługi, wprowadzono pomyślnego dopasowania między usługą identyfikatora URI i zakres identyfikatora URI, a czasami za pomocą reguł zakresu, które obsłużyć komplikacji dopasowania.</span><span class="sxs-lookup"><span data-stu-id="6aced-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6aced-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6aced-134">Parent Elements</span></span>  
  
|<span data-ttu-id="6aced-135">Element</span><span class="sxs-lookup"><span data-stu-id="6aced-135">Element</span></span>|<span data-ttu-id="6aced-136">Opis</span><span class="sxs-lookup"><span data-stu-id="6aced-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aced-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="6aced-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="6aced-138">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="6aced-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aced-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aced-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
