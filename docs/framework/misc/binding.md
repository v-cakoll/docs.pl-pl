---
title: "&lt;Powiązanie&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b9e0c7e077a9f47de6df31b00f4df320b845150
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
