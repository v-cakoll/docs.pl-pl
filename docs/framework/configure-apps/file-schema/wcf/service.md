---
title: "&lt;usługi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: "27"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f909fe64e8997a39519fbde2e476a324319f57d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicegt"></a>&lt;usługi&gt;
`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF). Zawiera ona także punkty końcowe, które udostępniają usługi.  
  
 \<System. ServiceModel >  
\<usługi >  
\<usługi >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|behaviorConfiguration|Ciąg zawierający nazwę zachowania zachowania, które ma być używany do utworzenia wystąpienia usługi. Nazwa zachowania musi być w zakresie w punkcie, który usługa została zdefiniowana. Wartością domyślną jest ciąg pusty.|  
|nazwa|Wymagany atrybut ciągu określający typ usługi zostać utworzone. To ustawienie musi są równoważne do prawidłowego typu. Format powinien być`Namespace.Class.`|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Kolekcja `endpoint` elementy, które udostępniają tej usługi.|  
|[\<host >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Określa hosta tego wystąpienia usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Element główny wszystkich elementów konfiguracji usługi WCF.|  
  
## <a name="remarks"></a>Uwagi  
 Usługi są zdefiniowane w `services` sekcji pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma własną `service` sekcji konfiguracji. W tej sekcji i jego zawartości definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.  
  
 `behaviorConfiguration` Element również jest opcjonalne. Identyfikuje zachowanie usługi używa. Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie, w tym samym pliku konfiguracji.  
  
 Każda usługa przedstawia jeden lub więcej punktów końcowych, które ma swój własny adres i powiązanie. Wszystkie powiązania używane w pliku konfiguracji musi być zdefiniowana w zakresie pliku. Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`. `name` Atrybut opisuje powiązania jest zdefiniowany w sekcji. `bindingConfiguration` Atrybut definiuje konfigurację w sekcji binding, która jest używana. Powiązania sekcji można określić kilka konfiguracji.  
  
## <a name="example"></a>Przykład  
 Jest to przykład konfiguracji usługi.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [Konfigurowanie usług](../../../../../docs/framework/wcf/configuring-services.md)
