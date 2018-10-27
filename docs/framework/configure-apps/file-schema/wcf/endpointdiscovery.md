---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 0dde8150632c5d8a7bcea3dbeffe70b380d3a322
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183844"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="dd2ed-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="dd2ed-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="dd2ed-103">Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="dd2ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd2ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd2ed-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-105">\<behaviors></span></span>  
<span data-ttu-id="dd2ed-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="dd2ed-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="dd2ed-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-107">\<behavior></span></span>  
<span data-ttu-id="dd2ed-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd2ed-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd2ed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd2ed-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd2ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd2ed-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd2ed-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd2ed-112">Attributes</span></span>  
  
|<span data-ttu-id="dd2ed-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dd2ed-113">Attribute</span></span>|<span data-ttu-id="dd2ed-114">Opis</span><span class="sxs-lookup"><span data-stu-id="dd2ed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd2ed-115">Włączone</span><span class="sxs-lookup"><span data-stu-id="dd2ed-115">enabled</span></span>|<span data-ttu-id="dd2ed-116">Wartość logiczna określająca czy odkrywanie jest włączone dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="dd2ed-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd2ed-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd2ed-118">Child Elements</span></span>  
  
|<span data-ttu-id="dd2ed-119">Element</span><span class="sxs-lookup"><span data-stu-id="dd2ed-119">Element</span></span>|<span data-ttu-id="dd2ed-120">Opis</span><span class="sxs-lookup"><span data-stu-id="dd2ed-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd2ed-121">\<zakresy ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="dd2ed-122">Kolekcja zakres identyfikatorów URI dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="dd2ed-123">Więcej niż jednego zakresu identyfikatorów URI może być skojarzony z jednym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="dd2ed-124">[\<Rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [z \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="dd2ed-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="dd2ed-125">Kolekcja elementów XML umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="dd2ed-126">\<typy ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-126">\<types></span></span>|<span data-ttu-id="dd2ed-127">Kolekcja interfejsów do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd2ed-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd2ed-128">Parent Elements</span></span>  
  
|<span data-ttu-id="dd2ed-129">Element</span><span class="sxs-lookup"><span data-stu-id="dd2ed-129">Element</span></span>|<span data-ttu-id="dd2ed-130">Opis</span><span class="sxs-lookup"><span data-stu-id="dd2ed-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd2ed-131">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="dd2ed-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dd2ed-132">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="dd2ed-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd2ed-133">Remarks</span></span>  
 <span data-ttu-id="dd2ed-134">Po dodaniu konfiguracji zachowanie punktu końcowego i za pomocą `enabled` ustawioną wartość atrybutu `true`, ten element konfiguracji umożliwia jego wykrywalność.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="dd2ed-135">Ponadto można użyć [ \<zakresy >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)element podrzędny do określania niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania, jak również [ \<rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) element podrzędny do określania niestandardowych metadanych, które powinny być publikowane wraz ze standardowego wykrywalny metadanych (EPR, ContractTypeName, BindingName, zakresu i identyfikatorze ListenURI).</span><span class="sxs-lookup"><span data-stu-id="dd2ed-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="dd2ed-136">Ten element konfiguracji jest zależny od [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element, który zapewnia kontrolę odnajdowanie w systemach z poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="dd2ed-137">Oznacza to, że ustawienia tego elementu są ignorowane w przypadku [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) nie jest obecny w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd2ed-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd2ed-138">Example</span></span>  
 <span data-ttu-id="dd2ed-139">W poniższym przykładzie konfiguracja określa filtrowania zakresów i metadane rozszerzenia do opublikowania dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dd2ed-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="dd2ed-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd2ed-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
