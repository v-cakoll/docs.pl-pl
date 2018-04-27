---
title: Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3834f48c407f799fc5fede17182f47652f49747f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="best-practices-for-queued-communication"></a>Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
W tym temacie przedstawiono zalecane praktyki dla komunikacji z obsługą kolejek w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. W poniższych sekcjach omówiono zalecane praktyki z punktu widzenia scenariusza.  
  
## <a name="fast-best-effort-queued-messaging"></a>Szybkie optymalnych w kolejce obsługi wiadomości  
 Scenariusze wymagające zapewnia oddzielenie, który obsługi wiadomości w kolejce i szybko i wysokiej wydajności wiadomości zapewnienia optymalnych Użyj nietransakcyjnej kolejki i ustaw <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> właściwości `false`.  
  
 Ponadto użytkownik może nie ponoszenia kosztów operacji zapisu na dysku przez ustawienie <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> właściwości `false`.  
  
 Zabezpieczenia mają wpływ na wydajność. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Zagadnienia dotyczące wydajności](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Niezawodne End-to-End w kolejce obsługi wiadomości  
 W poniższych sekcjach opisano najważniejsze wskazówki dotyczące scenariuszy, które wymagają end-to-end niezawodna obsługa komunikatów.  
  
### <a name="basic-reliable-transfer"></a>Transfer niezawodne podstawowe  
 Niezawodność end-to-end można ustawić <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> właściwości `true` zapewnienie transferu. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Ustawioną właściwość `true` lub `false` w zależności od wymagań (wartość domyślna to `true`). Ogólnie rzecz biorąc <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> właściwość jest ustawiona na `true` jako część niezawodności end-to-end. Naruszenia zabezpieczeń jest koszt wydajności, ale powoduje, że komunikat trwałe, aby komunikat nie zostaną utracone, jeśli wystąpiła awaria menedżera kolejek.  
  
### <a name="use-of-transactions"></a>Używanie transakcji  
 Aby zapewnić niezawodność end-to-end, należy użyć transakcji. `ExactlyOnce` gwarancje tylko zapewnić dostarczenie wiadomości do kolejki docelowej. Aby upewnić się, że komunikat jest odbierany, użyj transakcji. Bez transakcji Jeśli usługa ulegnie awarii, utracisz komunikat, który jest dostarczana, ale faktycznie jest dostarczany do aplikacji.  
  
### <a name="use-of-dead-letter-queues"></a>Użyj kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości upewnij się, że powiadamia komunikat nie zostanie dostarczona do kolejki docelowej. Możesz użyć kolejki utraconych wiadomości dostarczane przez system lub niestandardowej kolejki utraconych wiadomości. Ogólnie rzecz biorąc przy użyciu niestandardowej kolejki utraconych wiadomości jest najlepszym, ponieważ pozwala na wysyłanie wiadomości utraconych z jednej aplikacji do pojedynczej kolejki utraconych wiadomości. W przeciwnym razie wszystkich wiadomości utraconych wiadomości, które miało miejsce w przypadku wszystkich aplikacji uruchomionych w systemie są dostarczane do pojedynczej kolejki. Każda aplikacja musi następnie wyszukaj jednak kolejki utraconych wiadomości, można znaleźć wiadomości utraconych wiadomości, które mają zastosowanie do tej aplikacji. Czasami przy użyciu niestandardowej kolejki utraconych wiadomości nie jest to możliwe, takie jak, korzystając z usługi MSMQ 3.0.  
  
 Nie zaleca się wyłączenie kolejki utraconych wiadomości dla komunikacji niezawodnej na trasie.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Przy użyciu kolejki utraconych wiadomości do obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Użyj Poison komunikat — Obsługa  
 Poison komunikat — Obsługa zapewnia możliwość odzyskiwania danych po awarii do przetwarzania komunikatów.  
  
 Podczas korzystania z funkcji obsługi komunikatów poison, upewnij się, że <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> właściwość jest ustawiona na odpowiednią wartość. Ustawieniem dla niego <xref:System.ServiceModel.ReceiveErrorHandling.Drop> oznacza, że dane zostaną utracone. Z drugiej strony, ustawieniem dla niego <xref:System.ServiceModel.ReceiveErrorHandling.Fault> błędów hosta usługi, gdy wykryje Trująca wiadomość. Za pomocą usługi MSMQ w wersji 3.0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> jest najlepszą opcją, aby uniknąć utraty danych i przenieść Trująca wiadomość do końca. Za pomocą usługi MSMQ 4.0, <xref:System.ServiceModel.ReceiveErrorHandling.Move> jest zalecanym podejściem. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Przenosi skażone wiadomości z kolejki, więc usługa dalsze przetwarzanie nowych wiadomości. Usługa poison wiadomość można następnie oddzielnie przetworzyć Trująca wiadomość.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Uzyskanie wysokiej przepływności  
 Uzyskanie wysokiej przepływności na jeden punkt końcowy, użyj następującego polecenia:  
  
-   Wykonany, przetwarzanie wsadowe. Transakcyjnego przetwarzania wsadowego gwarantuje, że wiele komunikatów mogą być odczytywane w ramach jednej transakcji. Umożliwia to optymalne zatwierdzeń transakcji, zwiększa ogólną wydajność. Przetwarzanie wsadowe koszt jest to, że jeśli wystąpi błąd w pojedynczym komunikacie w partii, a następnie całą partię zostanie wycofana i komunikaty muszą być przetwarzane jedna aż bezpiecznie partii ponownie. W większości przypadków skażone wiadomości występują rzadko, dlatego tworzenie plików wsadowych jest preferowany sposób, aby zwiększyć wydajność systemu, zwłaszcza w przypadku innych menedżerowie zasobów, które uczestniczą w transakcji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Współbieżność. Współbieżność zwiększa przepustowość, ale współbieżności wpływa na rywalizacji do zasobów udostępnionych. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Ograniczenia przepustowości. Aby zoptymalizować wydajność ograniczyć liczbę komunikatów w potoku dyspozytora. Na przykład jak to zrobić, zobacz [ograniczania](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Podczas korzystania z przetwarzania wsadowego, należy pamiętać, że współbieżności i ograniczania przepustowości przełożyć na partie współbieżnych.  
  
 Aby osiągnąć wyższy przepływności i dostępności, użyj farma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, które zapoznały się z kolejki. Wymaga to, że wszystkie te usługi narazić ten sam kontrakt, w tym samym punkcie końcowym. To rozwiązanie farmy jest najlepsza dla aplikacji, które mają produkcji wysokiej szybkości wiadomości, ponieważ dzięki liczbę usług do wszystkich odczytywać z tej samej kolejki.  
  
 Podczas korzystania z farmy, należy pamiętać, usługa MSMQ 3.0 nie obsługuje zdalnego odczyty transakcyjne. MSMQ 4.0 obsługuje zdalne odczyty transakcyjne.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) i [różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Usługi kolejkowania wiadomości z jednostką pracy semantyki  
 W niektórych scenariuszach może być powiązane grupy wiadomości w kolejce i w związku z tym kolejności tych wiadomości jest znacząca. W takich scenariuszach przetwarzania grupy powiązane komunikaty razem jako pojedyncza jednostka: wszystkie komunikaty są przetwarzane pomyślnie albo żaden nie jest. Aby zaimplementować takie zachowanie, użyj sesji z kolejki.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Grupowanie wiadomości w kolejce w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Korelowanie wiadomości "żądanie-odpowiedź"  
 Chociaż kolejki są zwykle jednokierunkowe, w niektórych sytuacjach może zajść potrzeba dopasowania odpowiedzi otrzymanych na żądanie wysłane wcześniej. Jeśli potrzebujesz takie korelacji zaleca się stosowanie własnych nagłówek komunikatu protokołu SOAP, zawierający informacje o powiązaniu z komunikatem. Zazwyczaj nadawca dołącza ten nagłówek z komunikatem i odbiornik, podczas przetwarzania komunikatu i odpowiedzi z powrotem nowej wiadomości w kolejce odpowiedzi, dołączenie nadawcy wiadomości nagłówek, który zawiera informacje o powiązaniu, dlatego można nadawcy Określ komunikat odpowiedzi z komunikatu żądania.  
  
## <a name="integrating-with-non-wcf-applications"></a>Współdziałanie z aplikacjami z systemem innym niż WCF  
 Użyj `MsmqIntegrationBinding` składników podczas integrowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług lub klientom z systemem innym niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług lub klientów. Nienależących[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji mogą być napisane przy użyciu System.Messaging, COM +, Visual Basic lub C++ aplikacji usługi MSMQ.  
  
 Korzystając z `MsmqIntegrationBinding`, należy pamiętać o następujących czynności:  
  
-   A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] treść komunikatu nie jest taka sama jak treść wiadomości MSMQ. Podczas wysyłania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikatów za pomocą powiązania kolejkowanego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] treści wiadomości znajduje się wewnątrz wiadomości MSMQ. Infrastruktura usługi MSMQ jest oblivious do tych informacji dodatkowych; widzi ona tylko wiadomości MSMQ.  
  
-   `MsmqIntegrationBinding` obsługuje serializacji popularnych typów. Na podstawie typu serializacji, typ treści komunikat ogólny <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, przyjmuje parametry innego typu. Na przykład <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> wymaga `MsmqMessage\<byte[]>` i <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> wymaga `MsmqMessage<Stream>`.  
  
-   Serializacji XML można określić przy użyciu znanego typu `KnownTypes` atrybutu [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element, który jest następnie używany do określania, jak deserializować wiadomości XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Grupowanie komunikatów z obsługą kolejek w ramach sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Korzystanie z zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [Rozwiązywanie problemów obsługi komunikatów kolejek](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
