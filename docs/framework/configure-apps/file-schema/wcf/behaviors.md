---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926396"
---
# <a name="behaviors"></a>\<> zachowań
Ten element definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach i `serviceBehaviors`.  Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi. Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](endpointbehaviors.md)|Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.|  
|[\<> serviceBehaviors](servicebehaviors.md)|Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć elementu, `<remove>` aby usunąć określone zachowanie z kolekcji. W tym celu wystarczy podać nazwę zachowania do usunięcia w `name` atrybucie `<remove>` elementu.  Można również użyć elementu, `<clear>` aby upewnić się, że kolekcja zachowań zaczyna się pusta przez wyczyszczenie całej zawartości kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Konfigurowanie zachowań klienta](../../../wcf/configuring-client-behaviors.md)
- [Określanie zachowania klienta w czasie wykonywania](../../../wcf/specifying-client-run-time-behavior.md)
- [Określanie zachowania środowiska uruchomieniowego usługi](../../../wcf/specifying-service-run-time-behavior.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
