---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919050"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="1dffd-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="1dffd-101">\<endpointDiscovery></span></span>
<span data-ttu-id="1dffd-102">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="1dffd-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="1dffd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1dffd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1dffd-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="1dffd-104">\<behaviors></span></span>  
<span data-ttu-id="1dffd-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1dffd-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="1dffd-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="1dffd-106">\<behavior></span></span>  
<span data-ttu-id="1dffd-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="1dffd-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dffd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dffd-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dffd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1dffd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1dffd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1dffd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dffd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1dffd-111">Attributes</span></span>  
  
|<span data-ttu-id="1dffd-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1dffd-112">Attribute</span></span>|<span data-ttu-id="1dffd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1dffd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dffd-114">dostępny</span><span class="sxs-lookup"><span data-stu-id="1dffd-114">enabled</span></span>|<span data-ttu-id="1dffd-115">Wartość logiczna określająca, czy wykrywalność jest włączona w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="1dffd-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="1dffd-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="1dffd-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dffd-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1dffd-117">Child Elements</span></span>  
  
|<span data-ttu-id="1dffd-118">Element</span><span class="sxs-lookup"><span data-stu-id="1dffd-118">Element</span></span>|<span data-ttu-id="1dffd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1dffd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dffd-120">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="1dffd-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="1dffd-121">Kolekcja identyfikatorów URI zakresu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1dffd-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="1dffd-122">Więcej niż jeden identyfikator URI zakresu może być skojarzony z jednym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="1dffd-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="1dffd-123">rozszerzenia > [z \<endpointDiscovery >] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="1dffd-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="1dffd-124">Kolekcja elementów XML, która umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1dffd-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="1dffd-125">\<typy ></span><span class="sxs-lookup"><span data-stu-id="1dffd-125">\<types></span></span>|<span data-ttu-id="1dffd-126">Kolekcja interfejsów do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="1dffd-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dffd-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1dffd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1dffd-128">Element</span><span class="sxs-lookup"><span data-stu-id="1dffd-128">Element</span></span>|<span data-ttu-id="1dffd-129">Opis</span><span class="sxs-lookup"><span data-stu-id="1dffd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dffd-130">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="1dffd-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1dffd-131">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="1dffd-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="1dffd-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dffd-132">Remarks</span></span>  
 <span data-ttu-id="1dffd-133">Po dodaniu do konfiguracji zachowania punktu końcowego i z `enabled` atrybutem ustawionym na `true`, ten element konfiguracji umożliwia odnajdywanie.</span><span class="sxs-lookup"><span data-stu-id="1dffd-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="1dffd-134">Ponadto można użyć [ \<zakresów >](scopes.md)elementu podrzędnego, aby określić niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania, a także [ \<rozszerzenia >](extensions.md) elementu podrzędnego, aby określić niestandardowe metadane, które powinny być publikowane wraz ze standardowym odnajdywaniem metadanych (EPR, ContractTypeName, BindingName, Scope i ListenURI).</span><span class="sxs-lookup"><span data-stu-id="1dffd-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="1dffd-135">Ten element konfiguracji jest zależny od [ \<elementu > servicediscovery](servicediscovery.md) , który zapewnia kontrolę poziomu usług odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="1dffd-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="1dffd-136">Oznacza to, że ustawienia tego elementu są ignorowane, [ \<](servicediscovery.md) Jeśli w konfiguracji nie ma > servicediscovery.</span><span class="sxs-lookup"><span data-stu-id="1dffd-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dffd-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dffd-137">Example</span></span>  
 <span data-ttu-id="1dffd-138">Poniższy przykład konfiguracji określa zakresy filtrowania i metadane rozszerzenia do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1dffd-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="1dffd-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dffd-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
