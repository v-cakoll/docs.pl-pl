---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925585"
---
# <a name="findcriteria"></a><span data-ttu-id="1dc00-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="1dc00-101">\<findCriteria></span></span>
<span data-ttu-id="1dc00-102">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1dc00-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1dc00-103">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="1dc00-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="1dc00-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1dc00-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1dc00-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1dc00-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc00-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dc00-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dc00-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1dc00-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1dc00-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1dc00-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dc00-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1dc00-109">Attributes</span></span>  
  
|<span data-ttu-id="1dc00-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1dc00-110">Attribute</span></span>|<span data-ttu-id="1dc00-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1dc00-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dc00-112">czas trwania</span><span class="sxs-lookup"><span data-stu-id="1dc00-112">duration</span></span>|<span data-ttu-id="1dc00-113">Wartość TimeSpan, która określa maksymalny czas oczekiwania na odpowiedzi z usług w sieci.</span><span class="sxs-lookup"><span data-stu-id="1dc00-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="1dc00-114">Domyślny czas trwania wynosi 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="1dc00-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="1dc00-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="1dc00-115">maxResults</span></span>|<span data-ttu-id="1dc00-116">Liczba całkowita określająca maksymalną liczbę odpowiedzi od usług w sieci lub Internetu.</span><span class="sxs-lookup"><span data-stu-id="1dc00-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="1dc00-117">Jeśli zostaną odebrane maksymalne odpowiedzi przed upływem wartości określonej `duration` w atrybucie, kończy się operacja znajdowania.</span><span class="sxs-lookup"><span data-stu-id="1dc00-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="1dc00-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="1dc00-118">scopeMatchBy</span></span>|<span data-ttu-id="1dc00-119">Identyfikator URI, który określa zgodny algorytm do użycia podczas dopasowywania zakresów w komunikacie sondy z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="1dc00-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="1dc00-120">Istnieją pięć obsługiwanych reguł dopasowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="1dc00-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="1dc00-121">Jeśli nie określisz reguły dopasowywania zakresu, `ScopeMatchByPrefix` jest używana.</span><span class="sxs-lookup"><span data-stu-id="1dc00-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="1dc00-122">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="1dc00-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dc00-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1dc00-123">Child Elements</span></span>  
  
|<span data-ttu-id="1dc00-124">Element</span><span class="sxs-lookup"><span data-stu-id="1dc00-124">Element</span></span>|<span data-ttu-id="1dc00-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1dc00-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dc00-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="1dc00-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="1dc00-127">Kolekcja elementów konfiguracji, które zawierają nazwy typów kontraktu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1dc00-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="1dc00-128">\<rozszerzenia > \<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="1dc00-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="1dc00-129">Kolekcja obiektów elementu XML, które udostępniają rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1dc00-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="1dc00-130">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="1dc00-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="1dc00-131">Kolekcja obiektów, które zawierają bezwzględne identyfikatory URI, które są używane podczas operacji znajdowania do lokalizowania określonej usługi lub usług.</span><span class="sxs-lookup"><span data-stu-id="1dc00-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="1dc00-132">Jeśli określona usługa zostanie znaleziona, nastąpi pomyślne dopasowanie między identyfikatorem URI usługi i identyfikatorem URI zakresu, czasami z pomocą reguł zakresu, które obsługują komplikacje dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="1dc00-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dc00-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1dc00-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1dc00-134">Element</span><span class="sxs-lookup"><span data-stu-id="1dc00-134">Element</span></span>|<span data-ttu-id="1dc00-135">Opis</span><span class="sxs-lookup"><span data-stu-id="1dc00-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dc00-136">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1dc00-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1dc00-137">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="1dc00-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dc00-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dc00-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
