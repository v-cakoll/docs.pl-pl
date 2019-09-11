---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855169"
---
# <a name="findcriteria"></a><span data-ttu-id="8152e-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="8152e-101">\<findCriteria></span></span>
<span data-ttu-id="8152e-102">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8152e-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="8152e-103">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="8152e-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
<span data-ttu-id="8152e-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8152e-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8152e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="8152e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="8152e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="8152e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="8152e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="8152e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Kryteria znajdowania >**</span><span class="sxs-lookup"><span data-stu-id="8152e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8152e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="8152e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8152e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8152e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8152e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8152e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8152e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8152e-114">Attributes</span></span>  
  
|<span data-ttu-id="8152e-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8152e-115">Attribute</span></span>|<span data-ttu-id="8152e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8152e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8152e-117">czas trwania</span><span class="sxs-lookup"><span data-stu-id="8152e-117">duration</span></span>|<span data-ttu-id="8152e-118">Wartość TimeSpan, która określa maksymalny czas oczekiwania na odpowiedzi z usług w sieci.</span><span class="sxs-lookup"><span data-stu-id="8152e-118">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="8152e-119">Domyślny czas trwania wynosi 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="8152e-119">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="8152e-120">maxResults</span><span class="sxs-lookup"><span data-stu-id="8152e-120">maxResults</span></span>|<span data-ttu-id="8152e-121">Liczba całkowita określająca maksymalną liczbę odpowiedzi od usług w sieci lub Internetu.</span><span class="sxs-lookup"><span data-stu-id="8152e-121">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="8152e-122">Jeśli zostaną odebrane maksymalne odpowiedzi przed upływem wartości określonej `duration` w atrybucie, kończy się operacja znajdowania.</span><span class="sxs-lookup"><span data-stu-id="8152e-122">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="8152e-123">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="8152e-123">scopeMatchBy</span></span>|<span data-ttu-id="8152e-124">Identyfikator URI, który określa zgodny algorytm do użycia podczas dopasowywania zakresów w komunikacie sondy z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="8152e-124">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="8152e-125">Istnieją pięć obsługiwanych reguł dopasowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="8152e-125">There are five supported scope-matching rules.</span></span> <span data-ttu-id="8152e-126">Jeśli nie określisz reguły dopasowywania zakresu, `ScopeMatchByPrefix` jest używana.</span><span class="sxs-lookup"><span data-stu-id="8152e-126">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="8152e-127">Aby uzyskać więcej informacji na temat tego, zobacz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="8152e-127">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8152e-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8152e-128">Child Elements</span></span>  
  
|<span data-ttu-id="8152e-129">Element</span><span class="sxs-lookup"><span data-stu-id="8152e-129">Element</span></span>|<span data-ttu-id="8152e-130">Opis</span><span class="sxs-lookup"><span data-stu-id="8152e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8152e-131">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="8152e-131">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="8152e-132">Kolekcja elementów konfiguracji, które zawierają nazwy typów kontraktu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8152e-132">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="8152e-133">\<rozszerzenia > \<kryteria znajdowania ></span><span class="sxs-lookup"><span data-stu-id="8152e-133">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="8152e-134">Kolekcja obiektów elementu XML, które udostępniają rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8152e-134">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="8152e-135">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="8152e-135">\<scopes></span></span>](scopes.md)|<span data-ttu-id="8152e-136">Kolekcja obiektów, które zawierają bezwzględne identyfikatory URI, które są używane podczas operacji znajdowania do lokalizowania określonej usługi lub usług.</span><span class="sxs-lookup"><span data-stu-id="8152e-136">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="8152e-137">Jeśli określona usługa zostanie znaleziona, nastąpi pomyślne dopasowanie między identyfikatorem URI usługi i identyfikatorem URI zakresu, czasami z pomocą reguł zakresu, które obsługują komplikacje dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="8152e-137">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8152e-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8152e-138">Parent Elements</span></span>  
  
|<span data-ttu-id="8152e-139">Element</span><span class="sxs-lookup"><span data-stu-id="8152e-139">Element</span></span>|<span data-ttu-id="8152e-140">Opis</span><span class="sxs-lookup"><span data-stu-id="8152e-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8152e-141">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="8152e-141">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8152e-142">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="8152e-142">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8152e-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8152e-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
