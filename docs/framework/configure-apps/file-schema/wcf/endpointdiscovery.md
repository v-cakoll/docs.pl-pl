---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 125baba917a49135aaa426df2cfa1a4dbe8ac1e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700913"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="776ad-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="776ad-101">\<endpointDiscovery></span></span>
<span data-ttu-id="776ad-102">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="776ad-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="776ad-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="776ad-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="776ad-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="776ad-104">\<behaviors></span></span>  
<span data-ttu-id="776ad-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="776ad-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="776ad-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="776ad-106">\<behavior></span></span>  
<span data-ttu-id="776ad-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="776ad-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="776ad-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="776ad-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="776ad-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="776ad-109">Attributes and Elements</span></span>  
 <span data-ttu-id="776ad-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="776ad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="776ad-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="776ad-111">Attributes</span></span>  
  
|<span data-ttu-id="776ad-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="776ad-112">Attribute</span></span>|<span data-ttu-id="776ad-113">Opis</span><span class="sxs-lookup"><span data-stu-id="776ad-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="776ad-114">Włączone</span><span class="sxs-lookup"><span data-stu-id="776ad-114">enabled</span></span>|<span data-ttu-id="776ad-115">Wartość logiczna określająca czy odkrywanie jest włączone dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="776ad-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="776ad-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="776ad-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="776ad-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="776ad-117">Child Elements</span></span>  
  
|<span data-ttu-id="776ad-118">Element</span><span class="sxs-lookup"><span data-stu-id="776ad-118">Element</span></span>|<span data-ttu-id="776ad-119">Opis</span><span class="sxs-lookup"><span data-stu-id="776ad-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="776ad-120">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="776ad-120">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="776ad-121">Kolekcja zakres identyfikatorów URI dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="776ad-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="776ad-122">Więcej niż jednego zakresu identyfikatorów URI może być skojarzony z jednym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="776ad-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="776ad-123">[\<Rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="776ad-123">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="776ad-124">Kolekcja elementów XML umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="776ad-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="776ad-125">\<types></span><span class="sxs-lookup"><span data-stu-id="776ad-125">\<types></span></span>|<span data-ttu-id="776ad-126">Kolekcja interfejsów do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="776ad-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="776ad-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="776ad-127">Parent Elements</span></span>  
  
|<span data-ttu-id="776ad-128">Element</span><span class="sxs-lookup"><span data-stu-id="776ad-128">Element</span></span>|<span data-ttu-id="776ad-129">Opis</span><span class="sxs-lookup"><span data-stu-id="776ad-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="776ad-130">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="776ad-130">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="776ad-131">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="776ad-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="776ad-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="776ad-132">Remarks</span></span>  
 <span data-ttu-id="776ad-133">Po dodaniu konfiguracji zachowanie punktu końcowego i za pomocą `enabled` ustawioną wartość atrybutu `true`, ten element konfiguracji umożliwia jego wykrywalność.</span><span class="sxs-lookup"><span data-stu-id="776ad-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="776ad-134">Ponadto można użyć [ \<zakresy >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)element podrzędny do określania niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania, jak również [ \<rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) element podrzędny do określania niestandardowych metadanych, które powinny być publikowane wraz ze standardowego wykrywalny metadanych (EPR, ContractTypeName, BindingName, zakresu i identyfikatorze ListenURI).</span><span class="sxs-lookup"><span data-stu-id="776ad-134">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="776ad-135">Ten element konfiguracji jest zależny od [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, który zapewnia kontrolę odnajdowanie w systemach z poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="776ad-135">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="776ad-136">Oznacza to, że ustawienia tego elementu są ignorowane w przypadku [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) nie jest obecny w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="776ad-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="776ad-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="776ad-137">Example</span></span>  
 <span data-ttu-id="776ad-138">W poniższym przykładzie konfiguracja określa filtrowania zakresów i metadane rozszerzenia do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="776ad-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="776ad-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="776ad-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
