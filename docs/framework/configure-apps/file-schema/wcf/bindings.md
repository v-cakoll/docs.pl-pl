---
title: "&lt;powiązania&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed672ee918ad969feb8be6d20c9206e6b5d12278
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingsgt"></a>&lt;powiązania&gt;
Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych. Każdy wpis jest `binding` element, który można zidentyfikować przez jego unikatowy `name`. Usługi używają powiązania łącząc je za pomocą `name`. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-binding"></a>Powiązania dostarczane przez system  
 Powiązania dostarczane przez system neutralizują złożoność platformy WCF stosem obsługi wiadomości. Nie wymagają pełną kontrolę nad stosu aplikacji za pomocą powiązania dostarczane przez system. Atrybuty widoczne dla każdego powiązania dostarczane przez system są najbardziej odpowiednie dla scenariusza użycia adresów powiązania.  
  
 Sekcja konfiguracji dla każdego powiązania dostarczane przez system można określić kilka konfiguracje używane do konfigurowania wiązania. Każdej konfiguracji jest identyfikowany przez unikatową nazwę.  
  
 Nie jest możliwe do dodawania elementów lub atrybutów do powiązania dostarczane przez system. Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu. Istnieje możliwość definiowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązanie doskonale i dodaje kilka ustawień aplikacji użytkownik chce mają kontrolę nad.  
  
 Aby uzyskać listę powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-binding"></a>Powiązanie niestandardowe  
 Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF. Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie. Każdy element definiuje i konfiguruje jeden element stosu. Musi istnieć jeden i tylko jeden `transport` element w każdym niestandardowego powiązania. Bez tego elementu stosem obsługi wiadomości jest niekompletna.  
  
 Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości. Wymagana kolejność elementów stosu jest następujący:  
  
1.  Transakcje (opcjonalnie)  
  
2.  Niezawodnej obsługi komunikatów (opcjonalnie)  
  
3.  Zabezpieczeń (opcjonalnie)  
  
4.  Koder  
  
5.  Transportu  
  
 Powiązania niestandardowe są identyfikowane za pomocą ich `name` atrybutu. Aby uzyskać więcej informacji na powiązań niestandardowych, zobacz [niestandardowego powiązania](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
