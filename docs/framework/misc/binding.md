---
title: '&lt;Powiązanie&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltbindinggt"></a>&lt;Powiązanie&gt;
Można użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>Powiązania dostarczane przez system  
 Powiązania dostarczane przez system neutralizują złożoność platformy WCF stosem obsługi wiadomości. Nie wymagają pełną kontrolę nad stosu aplikacji za pomocą powiązania dostarczane przez system. Atrybuty widoczne dla każdego powiązania dostarczane przez system są najbardziej odpowiednie dla scenariusza użycia adresów powiązania.  
  
 Sekcja konfiguracji dla każdego powiązania dostarczane przez system można określić kilka konfiguracje używane do konfigurowania wiązania. Każdej konfiguracji jest identyfikowany przez unikatową nazwę.  
  
 Nie jest możliwe do dodawania elementów lub atrybutów do powiązania dostarczane przez system. Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu. Istnieje możliwość definiowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązanie doskonale i dodaje kilka ustawień aplikacji użytkownik chce mają kontrolę nad.  
  
## <a name="custom-binding"></a>Powiązanie niestandardowe  
 Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF. Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jeden element stosu. Musi istnieć jeden i tylko jeden `transport` element w każdym niestandardowego powiązania. Bez tego elementu stosem obsługi wiadomości jest niekompletna.  
  
 Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości. Zalecana kolejność elementów stosu jest następujący:  
  
1.  Transakcje (opcjonalnie)  
  
2.  Niezawodnej obsługi komunikatów (opcjonalnie)  
  
3.  Zabezpieczeń (opcjonalnie)  
  
4.  Koder  
  
5.  Transportu  
  
 Powiązania niestandardowe są identyfikowane za pomocą ich `name` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Powiązania](../../../docs/framework/wcf/bindings.md)  
 [Powiązania niestandardowe](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
