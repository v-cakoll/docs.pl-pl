---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936527"
---
# <a name="service"></a>\<service>
`service` Element zawiera ustawienia dla usługi Windows Communication Foundation (WCF). Zawiera również punkty końcowe, które uwidaczniają usługę.  
  
 \<system.ServiceModel>  
\<> usług  
\<service>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia usługi. Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa. Wartością domyślną jest ciąg pusty.|  
|nazwa|Wymagany atrybut ciągu, który określa typ usługi do wystąpienia. To ustawienie musi być równe prawidłowemu typowi. Format powinien być`Namespace.Class.`|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> punktu końcowego](endpoint-element.md)|Kolekcja `endpoint` elementów, które uwidaczniają tę usługę.|  
|[\<host>](host.md)|Określa hosta tego wystąpienia usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> usług](services.md)|Element główny wszystkich elementów konfiguracji WCF.|  
  
## <a name="remarks"></a>Uwagi  
 Usługi są zdefiniowane w `services` sekcji pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma swoją własną `service` sekcję konfiguracyjną. Ta sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.  
  
 `behaviorConfiguration` Element jest również opcjonalny. Identyfikuje zachowanie wykorzystywane przez usługę. Zachowanie określone w tym atrybucie musi łączyć się z zachowaniem w zakresie w tym samym pliku konfiguracyjnym.  
  
 Każda usługa ujawnia jeden lub więcej punktów końcowych, które mają własne adresy i powiązania. Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku. Powiązanie jest połączone z punktami końcowymi przez kombinację `name` atrybutów `bindingConfiguration`i. Ten `name` atrybut opisuje sekcję, w której jest zdefiniowane powiązanie. Ten `bindingConfiguration` atrybut określa, która konfiguracja w sekcji powiązania jest używana. Sekcja powiązania może definiować kilka konfiguracji.  
  
## <a name="example"></a>Przykład  
 Jest to przykład konfiguracji usługi.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [Konfigurowanie usług](../../../wcf/configuring-services.md)
