---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eaa3998d3d0b1642c0c92380ec1228eea69d4da8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700894"
---
# <a name="findcriteria"></a><span data-ttu-id="50373-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="50373-101">\<findCriteria></span></span>
<span data-ttu-id="50373-102">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania.</span><span class="sxs-lookup"><span data-stu-id="50373-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="50373-103">Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="50373-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="50373-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="50373-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="50373-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="50373-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50373-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="50373-106">Syntax</span></span>  
  
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
            </contractTypeNames>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50373-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50373-107">Attributes and Elements</span></span>  
 <span data-ttu-id="50373-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50373-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50373-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50373-109">Attributes</span></span>  
  
|<span data-ttu-id="50373-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="50373-110">Attribute</span></span>|<span data-ttu-id="50373-111">Opis</span><span class="sxs-lookup"><span data-stu-id="50373-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50373-112">czas trwania</span><span class="sxs-lookup"><span data-stu-id="50373-112">duration</span></span>|<span data-ttu-id="50373-113">Wartość przedziału czasu, który określa maksymalny czas oczekiwania na odpowiedzi z usług w sieci.</span><span class="sxs-lookup"><span data-stu-id="50373-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="50373-114">Domyślny czas trwania wynosi 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="50373-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="50373-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="50373-115">maxResults</span></span>|<span data-ttu-id="50373-116">Liczba całkowita określająca maksymalną liczbę odpowiedzi zaczekać z usług w sieci lub Internetu.</span><span class="sxs-lookup"><span data-stu-id="50373-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="50373-117">Jeśli maksymalna odpowiedzi są odbierane przed wartość określoną w `duration` atrybut upłynie zakończenia operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="50373-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="50373-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="50373-118">scopeMatchBy</span></span>|<span data-ttu-id="50373-119">Identyfikator URI, który określa algorytm dopasowania do użycia podczas dopasowywania zakresów w wiadomości sondy z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="50373-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="50373-120">Istnieje pięć obsługiwanych reguł dopasowania do zakresu.</span><span class="sxs-lookup"><span data-stu-id="50373-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="50373-121">Jeśli nie określisz regułę dopasowania w zakresie `ScopeMatchByPrefix` jest używany.</span><span class="sxs-lookup"><span data-stu-id="50373-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="50373-122">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="50373-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50373-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50373-123">Child Elements</span></span>  
  
|<span data-ttu-id="50373-124">Element</span><span class="sxs-lookup"><span data-stu-id="50373-124">Element</span></span>|<span data-ttu-id="50373-125">Opis</span><span class="sxs-lookup"><span data-stu-id="50373-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50373-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="50373-126">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="50373-127">Kolekcja elementów konfiguracji, które zawierają nazwy typu kontraktu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50373-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="50373-128">\<Rozszerzenia > z \<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="50373-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="50373-129">Kolekcja obiektów elementu XML, które udostępniają rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="50373-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="50373-130">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="50373-130">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="50373-131">Kolekcja obiektów zawierających bezwzględne identyfikatory URI, które są używane podczas operacji wyszukiwania, aby zlokalizować określonej usługi lub usług.</span><span class="sxs-lookup"><span data-stu-id="50373-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="50373-132">Jeśli zostanie znaleziony określonej usługi, udanych dopasowań stało się między usługą identyfikatora URI i zakres identyfikatora URI, a czasami za pomocą reguł zakresu, obsługujące komplikacji dopasowania.</span><span class="sxs-lookup"><span data-stu-id="50373-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50373-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50373-133">Parent Elements</span></span>  
  
|<span data-ttu-id="50373-134">Element</span><span class="sxs-lookup"><span data-stu-id="50373-134">Element</span></span>|<span data-ttu-id="50373-135">Opis</span><span class="sxs-lookup"><span data-stu-id="50373-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50373-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="50373-136">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="50373-137">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="50373-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50373-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50373-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
