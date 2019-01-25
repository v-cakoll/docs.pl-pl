---
title: '&lt;Powiązania&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb4fafda31205e2ce5efd01ab265fcacfa70bdf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539197"
---
# <a name="ltbindinggt"></a>&lt;Powiązania&gt;
Możesz użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>System-Provided Binding  
 Powiązania dostarczane przez system ukrywają złożoność architektury WCF stosem obsługi wiadomości. Aplikacje przy użyciu powiązania dostarczane przez system nie wymagają pełną kontrolę nad stosu. Atrybuty narażonych na każdego powiązania dostarczane przez system są tymi najbardziej odpowiednie dla scenariusza użycia adresów powiązania.  
  
 Sekcja konfiguracji dla każdego powiązania dostarczane przez system, można zdefiniować kilka konfiguracji używane do konfigurowania wiązania. Każdej konfiguracji jest identyfikowane przez unikatową nazwę.  
  
 Nie jest możliwe dodać elementy lub atrybuty do powiązania dostarczane przez system. Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu. Istnieje możliwość zdefiniowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązań doskonale i dodaje kilka ustawień aplikacji użytkownik chce, aby mieć kontrolę nad.  
  
## <a name="custom-binding"></a>Powiązanie niestandardowe  
 Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF. Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jeden element stosu. Musi istnieć jeden i tylko jeden `transport` elementu w każdej niestandardowego powiązania. Bez tego elementu stosem obsługi wiadomości jest niekompletna.  
  
 Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości. Zalecana kolejność elementów stosu jest następująca:  
  
1.  Transakcje (opcjonalnie)  
  
2.  Niezawodna obsługa komunikatów (opcjonalnie)  
  
3.  Zabezpieczenia (opcjonalnie)  
  
4.  Koder  
  
5.  Transport  
  
 Powiązania niestandardowe są identyfikowane przez ich `name` atrybutu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [Powiązania](../../../docs/framework/wcf/bindings.md)
- [Powiązania niestandardowe](../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
