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
# <a name="endpointdiscovery"></a>\<endpointDiscovery>
Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.  
  
\<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<endpointDiscovery>  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dostępny|Wartość logiczna określająca, czy wykrywalność jest włączona w tym punkcie końcowym. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zakresy >](scopes.md)|Kolekcja identyfikatorów URI zakresu dla punktu końcowego. Więcej niż jeden identyfikator URI zakresu może być skojarzony z jednym punktem końcowym.|  
|rozszerzenia > [z \<endpointDiscovery >] [ \<](extensions.md)|Kolekcja elementów XML, która umożliwia określenie niestandardowych metadanych do opublikowania dla punktu końcowego.|  
|\<typy >|Kolekcja interfejsów do wyszukania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
|||  
  
## <a name="remarks"></a>Uwagi  
 Po dodaniu do konfiguracji zachowania punktu końcowego i z `enabled` atrybutem ustawionym na `true`, ten element konfiguracji umożliwia odnajdywanie. Ponadto można użyć [ \<zakresów >](scopes.md)elementu podrzędnego, aby określić niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania, a także [ \<rozszerzenia >](extensions.md) elementu podrzędnego, aby określić niestandardowe metadane, które powinny być publikowane wraz ze standardowym odnajdywaniem metadanych (EPR, ContractTypeName, BindingName, Scope i ListenURI).  
  
 Ten element konfiguracji jest zależny od [ \<elementu > servicediscovery](servicediscovery.md) , który zapewnia kontrolę poziomu usług odnajdowania. Oznacza to, że ustawienia tego elementu są ignorowane, [ \<](servicediscovery.md) Jeśli w konfiguracji nie ma > servicediscovery.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguracji określa zakresy filtrowania i metadane rozszerzenia do opublikowania dla punktu końcowego.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
