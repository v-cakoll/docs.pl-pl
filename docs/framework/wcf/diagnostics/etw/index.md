---
title: Śledzenie analityczne za pomocą funkcji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: cff13439995d8a90da15b7afa15723f21574e35e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193729"
---
# <a name="analytic-tracing-with-etw"></a>Śledzenie analityczne za pomocą funkcji ETW
Śledzenie danych analitycznych usługi Windows Communication Foundation (WCF) oferuje możliwość przechwytywania informacji diagnostycznych podczas wykonywania usługi WCF. Zdarzenia śledzenia danych analitycznych programu WCF są emitowane w kluczowych punktach stos WCF, aby umożliwić Rozwiązywanie problemów z usług WCF w środowisku produkcyjnym. Śledzenie danych analitycznych do usługi WCF ma minimalny wpływ na wydajność serwera produktu obsługujący [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usług WCF, ponieważ te zdarzenia są bardzo wydajny sposób emitowane do sesji zdarzeń śledzenia dla Windows (ETW).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie śledzenia analitycznego](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 W tym artykule omówiono, jak działa śledzenie danych analitycznych programu WCF w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Dynamiczne włączanie śledzenia danych analitycznych](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 W tym artykule omówiono, jak włączyć lub wyłączyć śledzenie dynamicznie za pomocą funkcji ETW.  
  
 [Konfigurowanie śledzenia przepływu komunikatów](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 W tym artykule opisano sposób konfigurowania śledzenia przepływu komunikatów.  
  
 [Odwołanie do zdarzenia śledzenia analitycznego](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Przedstawia tabelę identyfikatory zdarzeń, ich poziomy zdarzenia, komunikaty o zdarzeniach i słów kluczowych.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
