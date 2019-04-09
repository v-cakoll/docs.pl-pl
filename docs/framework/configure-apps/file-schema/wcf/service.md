---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 68bddc01b02d9885b3f0fc4c2cbc5c3249de03f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197961"
---
# <a name="service"></a>\<service>
`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF). Zawiera ona także punktów końcowych, które udostępniają usługi.  
  
 \<system.ServiceModel>  
\<services>  
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
|behaviorConfiguration|Ciąg zawierający nazwę zachowania użytego do utworzenia wystąpienia usługi. Nazwa zachowania musi być w zakresie w punkcie, który jest zdefiniowany przez usługę. Wartością domyślną jest ciąg pusty.|  
|nazwa|Wymagany atrybut ciągu określający typ usługi, należy utworzyć wystąpienie. To ustawienie musi równoważne do prawidłowego typu. Powinna być w formacie `Namespace.Class.`|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Kolekcja `endpoint` elementy, które uwidaczniają tej usługi.|  
|[\<host>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Określa host to wystąpienie usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Element główny wszystkich elementów konfiguracji programu WCF.|  
  
## <a name="remarks"></a>Uwagi  
 Usługi są zdefiniowane w `services` sekcję pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma swoje własne `service` sekcji konfiguracji. W tej sekcji, a jego zawartością definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.  
  
 `behaviorConfiguration` Element jest również opcjonalne. Identyfikuje zachowanie usługi używa. Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie tego samego pliku konfiguracji.  
  
 Każda usługa udostępnia jeden lub więcej punktów końcowych, która ma swój własny adres i powiązanie. Wszystkie powiązania używane w pliku konfiguracyjnym musi być zdefiniowany w zakresie pliku. Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`. `name` Atrybutu w tym artykule opisano sekcji powiązania jest zdefiniowany w. `bindingConfiguration` Atrybut definiuje konfigurację, która w ramach sekcji powiązania jest używany. Sekcja powiązania można zdefiniować kilka konfiguracji.  
  
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
- [Konfigurowanie usług](../../../../../docs/framework/wcf/configuring-services.md)
