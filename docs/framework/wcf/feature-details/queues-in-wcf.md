---
title: Kolejki programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: e28c91a8cc1798a4d0cd690f72e503b687af0108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046453"
---
# <a name="queues-in-windows-communication-foundation"></a>Kolejki programu Windows Communication Foundation
W tematach w tej sekcji omówiono Windows Communication Foundation (WCF), obsługa kolejek. Usługi WCF zapewnia obsługę usługi kolejkowania wiadomości, wykorzystaniem Microsoft usługi kolejkowania komunikatów (wcześniej znane jako usługi MSMQ) jako transportu i umożliwia obsługę następujących scenariuszy:  
  
- Luźno powiązanych aplikacji. Wysyłanie aplikacje mogą wysyłać wiadomości do kolejki, bez znajomości czy aplikacja jest dostępne do przetwarzania wiadomości. Kolejka zapewnia niezależność przetwarzania, który umożliwia aplikacji wysyłającej wysyłać komunikaty do kolejki z szybkością, która nie zależy od szybkości aplikacje odbierające może przetwarzać komunikaty. Ogólna dostępność systemu zwiększa się podczas wysyłania wiadomości do kolejki jest nie ściśle powiązany przetwarzanie komunikatów.  
  
- Izolacja błędów. Aplikacje, wysyłanie i odbieranie komunikatów w kolejce może zakończyć się niepowodzeniem bez wpływu na siebie nawzajem. Jeśli na przykład, aplikacja zakończy się niepowodzeniem, wysyłanie aplikacja może kontynuować do wysyłania komunikatów do kolejki. Jeśli odbiorca jest ponownie uruchomiony, go przetwarzać komunikaty z kolejki. Izolacja błędów zwiększa ogólną niezawodność systemu i dostępności.  
  
- Wyrównywanie obciążenia. Aplikacje wysyłające może spowodować przeciążenie aplikacje odbierające przy użyciu komunikatów. Kolejki mogą zarządzać stawki produkcji i zużycia niedopasowanych wiadomości, aby odbiorca nie przeciążeniu.  
  
- Operacje odłączonych. Wysyłanie, odbieranie i przetwarzanie operacji może stać się rozłączona podczas komunikowania się za pośrednictwem sieci z dużym opóźnieniem lub ograniczoną dostępność sieci, takich jak w przypadku urządzeń przenośnych. Kolejki umożliwiają te operacje kontynuować, nawet gdy punkty końcowe są odłączone. Po ponownym ustanowieniu połączenia, kolejki przekazuje komunikaty odbierający aplikacji.  
  
 Funkcja kolejek w aplikacji WCF umożliwia standardowe powiązania, lub można utworzyć niestandardowego powiązania, jeśli jedno z powiązań standard nie spełnia wymagań. Aby uzyskać więcej informacji o odpowiednich powiązań standardowych i wybierz jedną, zobacz [jak: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami usługi kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Przegląd pojęć usługi kolejkowania komunikatów.  
  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Omówienie obsługi kolejki programu WCF.  
  
 [Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Opis sposobu użycia <xref:System.ServiceModel.NetMsmqBinding> klasy do komunikacji między klienta WCF i usługi WCF.  
  
 [Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Opis sposobu użycia <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> do komunikacji między aplikacjami usług WCF i usługi kolejkowania komunikatów.  
  
 [Grupowanie komunikatów z obsługą kolejek w ramach sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Wyjaśnia, jak należy zgrupować komunikatów w kolejce w celu ułatwienia przetwarzanie skorelowanych komunikatów przez aplikację odbierającą pojedynczego.  
  
 [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Wyjaśnia, jak partii komunikatów w ramach transakcji.  
  
 [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Wyjaśnia sposób obsługi błędów transferu i dostarczania wiadomości przy użyciu kolejki utraconych wiadomości i sposób przetwarzania komunikatów z kolejki utraconych wiadomości.  
  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Wyjaśnia sposób obsługi wiadomości (wiadomości, które przekroczyły maksymalną liczbę prób dostarczenia do aplikacji odbierającej).  
  
 [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Różnice w funkcji kolejek usługi WCF między [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 W tym artykule opisano sposób korzystania z zabezpieczeń transportu do zabezpieczenia wiadomości w kolejce.  
  
 [Korzystanie z zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Opisuje sposób używania zabezpieczeń wiadomości do zabezpieczenia wiadomości w kolejce.  
  
 [Rozwiązywanie problemów obsługi komunikatów kolejek](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Wyjaśnia, jak rozwiązać typowe problemy z kolejkowania.  
  
 [Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Wyjaśniono, że komunikacja kolejek najlepsze rozwiązania dotyczące korzystania z usługi WCF.  
