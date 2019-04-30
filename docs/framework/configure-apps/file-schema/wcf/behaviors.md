---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701232"
---
# <a name="behaviors"></a>\<zachowania >
Ten element definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każdej kolekcji definiuje zachowanie elementy używane przez punkty końcowe i usługi, odpowiednio. Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
|[\<endpointBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowane dla określonego punktu końcowego.|  
|[\<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanego dla określonej usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `<remove>` elementu do usunięcia określone zachowanie z kolekcji. Aby to zrobić, po prostu podać nazwę zachowania do usunięcia w `name` atrybutu `<remove>` elementu.  Można również użyć `<clear>` elementu, aby upewnić się, czy zbieranie zachowanie rozpoczyna się puste, czyszcząc się całą zawartość kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Konfigurowanie zachowań klienta](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Określanie zachowania klienta w czasie wykonywania](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Określanie zachowania środowiska uruchomieniowego usługi](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
