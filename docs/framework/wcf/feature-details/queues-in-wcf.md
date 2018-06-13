---
title: Kolejki programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: 96dfee3304369c300c40d595860898c51ff728aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496591"
---
# <a name="queues-in-windows-communication-foundation"></a>Kolejki programu Windows Communication Foundation
Tematy w tej sekcji omówiono w nim obsługę Windows Communication Foundation (WCF) kolejki. Usługi WCF zapewnia obsługę dla usługi kolejkowania wiadomości przez korzystanie z usług firmy Microsoft usługi kolejkowania komunikatów (wcześniej znane jako MSMQ) jako transportu i umożliwia realizację następujących scenariuszy:  
  
-   Luźno powiązanych aplikacji. Wysyłanie aplikacje mogą wysyłać wiadomości do kolejki, bez dokładnej znajomości, czy aplikacja jest dostępna do przetworzenia komunikatów. Kolejka zapewnia niezależność przetwarzania, umożliwiający wysyłanie aplikacji do wysyłania wiadomości do kolejki z szybkością nie zależy od tempa aplikacje odbierające może przetwarzać komunikatów. Ogólnej dostępności systemu zwiększa podczas wysyłania wiadomości do kolejki jest nie ściśle powiązane do przetwarzania komunikatów.  
  
-   Izolacja awarii. Aplikacje wysyłaniu lub odbieraniu wiadomości do kolejki może zakończyć się niepowodzeniem bez wpływu na siebie. Jeśli na przykład, aplikacja ulegnie awarii, aplikacja wysyłająca można nadal wysyłać wiadomości do kolejki. Jeśli odbiornik jest się ponownie, go przetworzyć wiadomości z kolejki. Błąd izolacji zwiększa ogólną niezawodności i dostępności.  
  
-   Wyrównywanie obciążenia. Aplikacje wysyłające można przeciąży aplikacje odbierające komunikatów. Kolejki można zarządzać szybkości przetwarzania produkcji i zużycia niedopasowanych komunikatów, aby odbiornik nie zalewowi.  
  
-   Operacje odłączone. Wysyłania, odbierania i operacji przetwarzania może stać się rozłączona podczas komunikacji za pośrednictwem sieci dużymi opóźnieniami lub ograniczoną dostępność sieci, takich jak w przypadku urządzeń przenośnych. Kolejki umożliwiają te operacje kontynuować, nawet wtedy, gdy punkty końcowe zostały odłączone. Po ponownym ustanowieniu połączenia, kolejki przesyła dalej wiadomości do aplikacji odbierającej.  
  
 Funkcja kolejek w aplikacji WCF, można użyć jednej z powiązań standardowych, lub można utworzyć niestandardowego powiązania, jeśli jedno z powiązań standardowych nie spełnia wymagań. Aby uzyskać więcej informacji na temat odpowiednich powiązań standardowych i wybierz jedną, zobacz [porady: wymiany komunikatów z punktami końcowymi WCF i aplikacji usługi kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Aby uzyskać więcej informacji o tworzeniu niestandardowych powiązań, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Omówienie koncepcji usługi kolejkowania komunikatów.  
  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Przegląd obsługi kolejki programu WCF.  
  
 [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Wyjaśniono, jak używać <xref:System.ServiceModel.NetMsmqBinding> klasy do komunikacji między klienta WCF i usługi WCF.  
  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Wyjaśniono, jak używać <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> do komunikacji między aplikacjami WCF i usługę kolejkowania komunikatów.  
  
 [Grupowanie komunikatów z obsługą kolejek w ramach sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Wyjaśniono, jak wiadomości w kolejce ułatwiające przetwarzania komunikatów skorelowane przez aplikację odbierającą jednej grupy.  
  
 [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Wyjaśniono, jak partii komunikatów w ramach transakcji.  
  
 [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Opisano sposób obsługi błędów transferu i dostarczania wiadomości przy użyciu kolejki utraconych wiadomości oraz do przetwarzania komunikatów z kolejki utraconych wiadomości.  
  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Wyjaśnia sposób obsługi wiadomości (wiadomości, które przekroczyły maksymalną liczbę prób dostarczenia do aplikacji odbierającej).  
  
 [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Zawiera podsumowanie różnic w funkcji WCF kolejek między [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Opisuje sposób użyć zabezpieczeń transportu do zabezpieczenia wiadomości w kolejce.  
  
 [Korzystanie z zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Opisuje sposób skorzystaj z zabezpieczeń wiadomości w celu zabezpieczenia wiadomości w kolejce.  
  
 [Rozwiązywanie problemów obsługi komunikatów kolejek](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Wyjaśniono, jak rozwiązać typowe problemy z kolejkowania wiadomości.  
  
 [Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Wyjaśniono, że najlepsze rozwiązania dotyczące używania usługi WCF w kolejce komunikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kolejkowania komunikatów](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
