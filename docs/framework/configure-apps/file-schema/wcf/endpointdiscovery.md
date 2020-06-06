---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398022"
---
# \<endpointDiscovery>
<span data-ttu-id="ceb0e-101">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="ceb0e-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="ceb0e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceb0e-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ceb0e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ceb0e-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceb0e-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ceb0e-105">Attributes</span></span>  
  
|<span data-ttu-id="ceb0e-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ceb0e-106">Attribute</span></span>|<span data-ttu-id="ceb0e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb0e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ceb0e-108">enabled</span><span class="sxs-lookup"><span data-stu-id="ceb0e-108">enabled</span></span>|<span data-ttu-id="ceb0e-109">Wartość logiczna określająca, czy wykrywalność jest włączona w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="ceb0e-110">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceb0e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ceb0e-111">Child Elements</span></span>  
  
|<span data-ttu-id="ceb0e-112">Element</span><span class="sxs-lookup"><span data-stu-id="ceb0e-112">Element</span></span>|<span data-ttu-id="ceb0e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb0e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="ceb0e-114">Kolekcja identyfikatorów URI zakresu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="ceb0e-115">Więcej niż jeden identyfikator URI zakresu może być skojarzony z jednym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="ceb0e-116">[\<extensions>](extensions.md)[z \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="ceb0e-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="ceb0e-117">Kolekcja elementów XML, która umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="ceb0e-118">Kolekcja interfejsów do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceb0e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ceb0e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ceb0e-120">Element</span><span class="sxs-lookup"><span data-stu-id="ceb0e-120">Element</span></span>|<span data-ttu-id="ceb0e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb0e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ceb0e-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ceb0e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ceb0e-123">Remarks</span></span>  
 <span data-ttu-id="ceb0e-124">Po dodaniu do konfiguracji zachowania punktu końcowego i z `enabled` atrybutem ustawionym na `true` , ten element konfiguracji umożliwia odnajdywanie.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="ceb0e-125">Ponadto można użyć [\<scopes>](scopes.md) elementu podrzędnego, aby określić niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania, a także [\<extensions>](extensions.md) element podrzędny, aby określić niestandardowe metadane, które powinny być publikowane wraz ze standardowym odnajdywaniem metadanych (EPR, ContractTypeName, BindingName, Scope i ListenUri).</span><span class="sxs-lookup"><span data-stu-id="ceb0e-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="ceb0e-126">Ten element konfiguracji zależy od [\<serviceDiscovery>](servicediscovery.md) elementu, który zapewnia kontrolę poziomu usługi odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="ceb0e-127">Oznacza to, że ustawienia tego elementu są ignorowane, jeśli [\<serviceDiscovery>](servicediscovery.md) nie są obecne w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceb0e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ceb0e-128">Example</span></span>  
 <span data-ttu-id="ceb0e-129">Poniższy przykład konfiguracji określa zakresy filtrowania i metadane rozszerzenia do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ceb0e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ceb0e-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
