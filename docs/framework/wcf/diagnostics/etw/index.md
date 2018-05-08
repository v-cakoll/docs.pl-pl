---
title: Śledzenie analityczne za pomocą funkcji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: a0e3e3d27283e588b161e2209c5a682558d18f79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="analytic-tracing-with-etw"></a>Śledzenie analityczne za pomocą funkcji ETW
Śledzenie analityczne Windows Communication Foundation (WCF) daje możliwość przechwytywania informacji diagnostycznych podczas wykonywania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zdarzenia śledzenia analitycznego są emitowane w punktach klucza [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stos, aby umożliwić rozwiązywania problemów z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług w środowisku produkcyjnym. Śledzenie analityczne dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług ma minimalny wpływ na wydajność serwera produktu obsługującego [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług te zdarzenia są bardzo wydajnie wysyłanego do sesji zdarzeń śledzenia zdarzeń systemu Windows (ETW).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie śledzenia analitycznego](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 W tym artykule omówiono sposób [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] śledzenie analityczne działa w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Dynamiczne włączanie śledzenia danych analitycznych](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 W tym artykule omówiono sposób włączyć lub wyłączyć śledzenie dynamicznie za pomocą funkcji ETW.  
  
 [Konfigurowanie śledzenia przepływu komunikatów](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Zawiera opis sposobu konfigurowania śledzenia przepływu komunikatów.  
  
 [Odwołanie do zdarzenia śledzenia analitycznego](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Przedstawia tabelę zdarzeń identyfikatorów ich poziomów zdarzeń, komunikaty o zdarzeniach i słów kluczowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
