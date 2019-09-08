---
title: Śledzenie analityczne za pomocą funkcji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798092"
---
# <a name="analytic-tracing-with-etw"></a>Śledzenie analityczne za pomocą funkcji ETW
Śledzenie analityczne Windows Communication Foundation (WCF) oferuje sposób przechwytywania informacji diagnostycznych podczas wykonywania usługi WCF. Zdarzenia śledzenia analitycznego WCF są emitowane w kluczowych punktach w stosie WCF, aby umożliwić Rozwiązywanie problemów z usługami WCF w środowisku produkcyjnym. Śledzenie analityczne dla usług WCF ma minimalny wpływ na wydajność serwera produktu, który obsługuje [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usługi WCF, ponieważ te zdarzenia są bardzo wydajnie emitowane do sesji śledzenia zdarzeń systemu Windows (ETW).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie śledzenia analitycznego](analytic-tracing-overview.md)  
 W [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]tym artykule omówiono sposób działania śledzenia analitycznego WCF.  
  
 [Dynamiczne włączanie śledzenia danych analitycznych](dynamically-enabling-analytic-tracing.md)  
 W tym artykule omówiono sposób dynamicznego włączania lub wyłączania śledzenia przy użyciu funkcji ETW.  
  
 [Konfigurowanie śledzenia przepływu komunikatów](configuring-message-flow-tracing.md)  
 Opisuje sposób konfigurowania śledzenia przepływu komunikatów.  
  
 [Odwołanie do zdarzenia śledzenia analitycznego](analytic-trace-event-reference.md)  
 Pokazuje tabelę identyfikatorów zdarzeń z ich poziomami zdarzeń, komunikatami zdarzeń i słowami kluczowymi.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
