---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398022"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="99735-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="99735-101">\<endpointDiscovery></span></span>
<span data-ttu-id="99735-102">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="99735-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="99735-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="99735-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99735-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="99735-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="99735-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="99735-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="99735-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="99735-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="99735-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="99735-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="99735-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="99735-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99735-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="99735-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99735-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99735-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99735-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99735-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99735-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99735-112">Attributes</span></span>  
  
|<span data-ttu-id="99735-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99735-113">Attribute</span></span>|<span data-ttu-id="99735-114">Opis</span><span class="sxs-lookup"><span data-stu-id="99735-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99735-115">dostępny</span><span class="sxs-lookup"><span data-stu-id="99735-115">enabled</span></span>|<span data-ttu-id="99735-116">Wartość logiczna określająca, czy wykrywalność jest włączona w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="99735-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="99735-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="99735-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99735-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99735-118">Child Elements</span></span>  
  
|<span data-ttu-id="99735-119">Element</span><span class="sxs-lookup"><span data-stu-id="99735-119">Element</span></span>|<span data-ttu-id="99735-120">Opis</span><span class="sxs-lookup"><span data-stu-id="99735-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99735-121">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="99735-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="99735-122">Kolekcja identyfikatorów URI zakresu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="99735-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="99735-123">Więcej niż jeden identyfikator URI zakresu może być skojarzony z jednym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="99735-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="99735-124">rozszerzenia > [z \<endpointDiscovery >] [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="99735-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="99735-125">Kolekcja elementów XML, która umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="99735-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="99735-126">\<typy ></span><span class="sxs-lookup"><span data-stu-id="99735-126">\<types></span></span>|<span data-ttu-id="99735-127">Kolekcja interfejsów do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="99735-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99735-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99735-128">Parent Elements</span></span>  
  
|<span data-ttu-id="99735-129">Element</span><span class="sxs-lookup"><span data-stu-id="99735-129">Element</span></span>|<span data-ttu-id="99735-130">Opis</span><span class="sxs-lookup"><span data-stu-id="99735-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99735-131">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="99735-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="99735-132">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="99735-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="99735-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99735-133">Remarks</span></span>  
 <span data-ttu-id="99735-134">Po dodaniu do konfiguracji zachowania punktu końcowego i z `enabled` atrybutem ustawionym na `true`, ten element konfiguracji umożliwia odnajdywanie.</span><span class="sxs-lookup"><span data-stu-id="99735-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="99735-135">Ponadto można użyć [ \<zakresów >](scopes.md)elementu podrzędnego, aby określić niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania, a także [ \<rozszerzenia >](extensions.md) elementu podrzędnego, aby określić niestandardowe metadane, które powinny być publikowane wraz ze standardowym odnajdywaniem metadanych (EPR, ContractTypeName, BindingName, Scope i ListenURI).</span><span class="sxs-lookup"><span data-stu-id="99735-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="99735-136">Ten element konfiguracji jest zależny od [ \<elementu > servicediscovery](servicediscovery.md) , który zapewnia kontrolę poziomu usług odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="99735-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="99735-137">Oznacza to, że ustawienia tego elementu są ignorowane, [ \<](servicediscovery.md) Jeśli w konfiguracji nie ma > servicediscovery.</span><span class="sxs-lookup"><span data-stu-id="99735-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99735-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="99735-138">Example</span></span>  
 <span data-ttu-id="99735-139">Poniższy przykład konfiguracji określa zakresy filtrowania i metadane rozszerzenia do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="99735-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99735-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99735-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
