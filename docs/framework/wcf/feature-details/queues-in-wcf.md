---
title: Kolejki programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: e921084ed28cb4e846cb269e57e58a194e9437a5
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837340"
---
# <a name="queues-in-windows-communication-foundation"></a>Kolejki programu Windows Communication Foundation
W tematach w tej sekcji omówiono obsługę Windows Communication Foundation (WCF) dla kolejek. Funkcja WCF zapewnia obsługę kolejkowania, wykorzystując usługę kolejkowania komunikatów firmy Microsoft (wcześniej znaną jako usługa MSMQ) jako Transport i udostępnia następujące scenariusze:  
  
- Połączone aplikacje. Wysyłanie aplikacji może wysyłać komunikaty do kolejek bez konieczności dowiedzieć się, czy aplikacja do odbioru jest dostępna do przetwarzania wiadomości. Kolejka zapewnia niezależność przetwarzania, która umożliwia aplikacji wysyłającej wysyłanie komunikatów do kolejki według stawki, która nie jest zależna od tego, jak szybko aplikacje do odbioru mogą przetwarzać komunikaty. Ogólna dostępność systemu wzrasta, gdy wysyłanie komunikatów do kolejki nie jest ściśle sprzężone z przetwarzaniem komunikatów.  
  
- Izolacja niepowodzeń. Aplikacje wysyłające lub otrzymujące komunikaty do kolejki mogą kończyć się niepowodzeniem bez wpływania na siebie nawzajem. Jeśli na przykład aplikacja otrzymująca nie powiedzie się, aplikacja wysyłająca może kontynuować wysyłanie komunikatów do kolejki. Po ponownym uruchomieniu odbiornik może przetwarzać komunikaty z kolejki. Izolacja awaryjna zwiększa ogólną niezawodność i dostępność systemu.  
  
- Wyrównywanie obciążenia. Wysyłanie aplikacji może przeciążać aplikacje wiadomościami. Kolejki mogą zarządzać niezgodnymi stawkami produkcyjnymi i zużycie komunikatów, aby odbiorca nie mógł go przeciążyć.  
  
- Operacje rozłączone. Operacje wysyłania, otrzymywania i przetwarzania mogą zostać rozłączone podczas komunikacji z sieciami o dużej opóźnieniu lub sieciami o ograniczonej dostępności, na przykład w przypadku urządzeń przenośnych. Kolejki umożliwiają kontynuowanie tych operacji, nawet gdy punkty końcowe są rozłączone. Gdy połączenie zostanie nawiązane, kolejka przekazuje komunikaty do aplikacji odbiorczej.  
  
 Aby użyć funkcji Queues w aplikacji WCF, można użyć jednego ze standardowych powiązań lub utworzyć niestandardowe powiązanie, jeśli jedno z powiązań standardowych nie spełnia wymagań. Aby uzyskać więcej informacji o odpowiednich powiązaniach standardowych i sposobach ich wyboru, zobacz [How to: Exchange messages with Endpoints i Applications kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Omówienie pojęć dotyczących usługi kolejkowania komunikatów.  
  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Omówienie obsługi kolejki WCF.  
  
 [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Wyjaśnia, w jaki sposób używać klasy <xref:System.ServiceModel.NetMsmqBinding> do komunikacji między klientem programu WCF a usługą WCF.  
  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Wyjaśnia, w jaki sposób używać <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> do komunikacji między aplikacjami WCF i kolejkowania komunikatów.  
  
 [Grupowanie komunikatów z obsługą kolejek w ramach sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Wyjaśnia, jak grupować komunikaty w kolejce, aby ułatwić przetwarzanie skorelowanych komunikatów przez jedną aplikację do odebrania.  
  
 [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Wyjaśnia, jak należy wykonać wsadowe wiadomości w transakcji.  
  
 [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Wyjaśnia, jak obsługiwać błędy transferu i dostarczania komunikatów za pomocą kolejek utraconych wiadomości oraz jak przetwarzać komunikaty z kolejki utraconych list.  
  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Wyjaśnia, jak obsługiwać trujące komunikaty (komunikaty, które przekroczyły maksymalną liczbę prób dostarczenia do aplikacji do odebrania).  
  
 [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Podsumowuje różnice w funkcjach kolejek WCF między systemem Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Opisuje sposób korzystania z zabezpieczeń transportu w celu zabezpieczenia komunikatów umieszczonych w kolejce.  
  
 [Korzystanie z zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Opisuje sposób korzystania z zabezpieczeń komunikatów w celu zabezpieczenia komunikatów umieszczonych w kolejce.  
  
 [Rozwiązywanie problemów obsługi komunikatów kolejek](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Wyjaśnia, jak rozwiązywać typowe problemy z kolejką.  
  
 [Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Zawiera opis najlepszych rozwiązań dotyczących używania komunikacji kolejkowanej WCF.  
