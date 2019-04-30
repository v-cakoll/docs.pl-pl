---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 479941593b1abefe637525703140b02917c6692b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704443"
---
# <a name="bindings"></a>\<powiązania >

Możesz użyć `bindings` element, aby skonfigurować kolekcję powiązań standardowych i niestandardowych dla usługi Windows Communication Foundation (WCF). Każdy wpis jest `binding` element, który może być określony przez jego unikatowy `name`. Usługi używają powiązania, łącząc je za pomocą `name`. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-bindings"></a>powiązania dostarczane przez system
 
 Powiązania dostarczane przez system ukrywają złożoność architektury WCF stosem obsługi wiadomości. Aplikacje przy użyciu powiązania dostarczane przez system nie wymagają pełną kontrolę nad stosu. Atrybuty narażonych na każdego powiązania dostarczane przez system są tymi najbardziej odpowiednie dla scenariusza użycia adresów powiązania.  
  
 Sekcja konfiguracji dla każdego powiązania dostarczane przez system, można zdefiniować kilka konfiguracji używane do konfigurowania wiązania. Każdej konfiguracji jest identyfikowane przez unikatową nazwę.  
  
 Nie można dodać elementów lub atrybutów do powiązania dostarczane przez system. Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w [niestandardowego powiązania](#custom-bindings) sekcji. Istnieje możliwość zdefiniowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązań doskonale i dodaje kilka ustawień aplikacji użytkownik chce, aby mieć kontrolę nad.  
  
 Aby uzyskać listę powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe

 Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF. Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jednego elementu stosu. Musi istnieć jeden i tylko jeden `transport` elementu w każdej niestandardowego powiązania. Bez tego elementu stosem obsługi wiadomości jest niekompletna.  
  
 Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości. Wymagane kolejność elementów stosu jest następująca:  
  
1. Transakcje (opcjonalnie)  
  
2. Niezawodna obsługa komunikatów (opcjonalnie)  
  
3. Zabezpieczenia (opcjonalnie)  
  
4. Koder  
  
5. Transport  
  
 Powiązania niestandardowe są identyfikowane przez ich `name` atrybutu. Aby uzyskać więcej informacji dotyczących powiązań niestandardowych, zobacz [powiązań niestandardowych](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
