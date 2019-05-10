---
title: Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: b2f64faab6df678182fb39174c8a558b298a8748
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584984"
---
# <a name="best-practices-for-queued-communication"></a>Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
Ten temat zawiera zalecane praktyki dotyczące komunikacji z obsługą kolejek w Windows Communication Foundation (WCF). W poniższych sekcjach omówiono zalecane praktyki z punktu widzenia scenariusza.  
  
## <a name="fast-best-effort-queued-messaging"></a>Szybkie optymalny w kolejce komunikatów  
 Dla scenariuszy, które wymagają zapewnia oddzielenie, który obsługi komunikatów w kolejce i szybko, o wysokiej wydajności, obsługa komunikatów za pomocą największej staranności gwarancje, użyj nietransakcyjnej kolejki i ustawić <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> właściwość `false`.  
  
 Ponadto, możesz nie ponosić kosztów operacji zapisu na dysku, ustawiając <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> właściwość `false`.  
  
 Zabezpieczenia mają wpływ na wydajność. Aby uzyskać więcej informacji, zobacz [zagadnienia związane z wydajnością](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Niezawodne End-to-End w kolejce komunikatów  
 W poniższych sekcjach opisano zalecane praktyki dla scenariuszy, które wymagają niezawodną obsługę komunikatów end-to-end.  
  
### <a name="basic-reliable-transfer"></a>Podstawowe niezawodne transferu  
 Niezawodność end-to-end, można ustawić <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> właściwość `true` zapewnienie transferu. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Właściwość może być ustawiona na `true` lub `false` w zależności od wymagań (wartość domyślna to `true`). Ogólnie rzecz biorąc <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> właściwość jest ustawiona na `true` jako część niezawodność end-to-end. Naruszenia zabezpieczeń jest spadek wydajności, ale sprawia, że komunikat trwałe, aby wiadomość nie zostaną utracone w przypadku awarii menedżera kolejek.  
  
### <a name="use-of-transactions"></a>Stosowanie transakcji  
 Aby zapewnić niezawodność end-to-end, należy użyć transakcji. `ExactlyOnce` gwarancje tylko upewnij się, że komunikaty są dostarczane do kolejki docelowej. Aby upewnić się, że wiadomość zostaje odebrana, należy użyć transakcji. Bez transakcji Jeśli usługa ulegnie awarii, utraty komunikat, który jest dostarczany, ale faktycznie jest dostarczane do aplikacji.  
  
### <a name="use-of-dead-letter-queues"></a>Użyj kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości upewnij się, że otrzymasz powiadomienie, jeśli komunikat nie zostanie dostarczona do kolejki docelowej. Można użyć kolejki utraconych wiadomości dostarczanych przez system lub niestandardowe kolejki utraconych wiadomości. Ogólnie rzecz biorąc przy użyciu niestandardowych kolejki utraconych wiadomości jest najlepszy, ponieważ pozwala na wysyłanie wiadomości utraconych komunikatów z jednej aplikacji do pojedynczej kolejki utraconych wiadomości. W przeciwnym razie wszystkie wiadomości utraconych występujących dla wszystkich aplikacji uruchomionych w systemie są dostarczane do pojedynczej kolejki. Każda aplikacja musi następnie wyszukiwania do kolejki utraconych wiadomości można znaleźć utracone wiadomości, które mają zastosowanie do tej aplikacji. Czasami za pomocą niestandardowych kolejki utraconych wiadomości jest niemożliwe, takie jak podczas korzystania z usługi MSMQ 3.0.  
  
 Nie zaleca się wyłączenie kolejki utraconych wiadomości komunikacji niezawodnej end-to-end.  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu kolejki utraconych wiadomości, do obsługi błędów transferu](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Korzystanie z Poison postępowanie  
 Obsługa komunikatów poison umożliwia odzyskiwanie po awarii do przetwarzania komunikatów.  
  
 Podczas korzystania z funkcji obsługi komunikatów poison, upewnij się, że <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> właściwość jest ustawiona na odpowiednią wartość. Ustawienie <xref:System.ServiceModel.ReceiveErrorHandling.Drop> oznacza, że dane zostaną utracone. Z drugiej strony, ustawieniem dla niego <xref:System.ServiceModel.ReceiveErrorHandling.Fault> błędów hosta usługi w razie wykrycia, zarządzanie skażonymi komunikatami. Za pomocą MSMQ 3.0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> jest to najlepsze rozwiązanie, aby uniknąć utraty danych, a następnie przenieść Zarządzanie skażonymi komunikatami na bok. Za pomocą usługi MSMQ 4.0, <xref:System.ServiceModel.ReceiveErrorHandling.Move> przedstawia zalecane podejście. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Przenosi uszkodzone kolejką komunikatu z kolejki, dzięki czemu usługa może w dalszym ciągu przetwarzać nowych wiadomości. Usługa poison wiadomość można następnie przetworzyć Zarządzanie skażonymi komunikatami oddzielnie.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Uzyskanie wysokiej przepływności  
 Aby osiągnąć wysoką przepływność w jednym punkcie końcowym, użyj następującego polecenia:  
  
- Wykonany, przetwarzanie wsadowe. Transakcyjnego przetwarzania wsadowego gwarantuje, że wiele komunikatów mogą być odczytywane w ramach jednej transakcji. Powoduje to zoptymalizowanie zatwierdzeń transakcji, zwiększa ogólną wydajność. Koszt przetwarzanie wsadowe jest to, że jeśli wystąpi awaria w pojedynczym komunikacie w ramach partii, a następnie całą partię zostanie wycofana i komunikaty muszą być przetworzone pojedynczo, dopóki nie jest bezpieczne partii ponownie. W większości przypadków skażone komunikaty są rzadkie, więc przetwarzania wsadowego jest preferowany sposób, aby zwiększyć wydajność systemu, zwłaszcza w przypadku innych menedżerów zasobów, które uczestniczą w transakcji. Aby uzyskać więcej informacji, zobacz [tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
- Współbieżność. Współbieżność zwiększa przepustowość, ale współbieżności będzie także miała wpływ rywalizacji o zasoby do udostępnionych zasobów. Aby uzyskać więcej informacji, zobacz [współbieżności](../../../../docs/framework/wcf/samples/concurrency.md).  
  
- Ograniczanie przepustowości. Aby uzyskać optymalną wydajność ograniczać liczbę komunikatów w potoku dyspozytora. Na przykład jak to zrobić, zobacz [ograniczania](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Korzystając z dzielenia na partie, należy pamiętać, że współbieżności i ograniczania przepustowości przełożyć na partie współbieżnych.  
  
 Aby osiągnąć wyższą przepustowość i dostępność, należy użyć farmy usług WCF, które odczytany z kolejki. Wymaga to, że wszystkie te usługi Udostępnianie tej samej umowy na ten sam punkt końcowy. Podejście farmy jest najlepsza dla aplikacji, które mają produkcyjne o wysokiej szybkości komunikatów, ponieważ umożliwia wielu usług dla wszystkich odczytu z tej samej kolejki.  
  
 Korzystając z farmy serwerów, należy pamiętać, usługa MSMQ 3.0 nie obsługuje zdalnego transakcyjne operacje odczytu. Usługa MSMQ 4.0 obsługuje zdalnego transakcyjne operacje odczytu.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) i [różnice w funkcjach kolejkowania w Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Usługi kolejkowania wiadomości z jednostką pracy semantyki  
 W niektórych scenariuszach mogą być związane z grupą komunikatów w kolejce i w związku z tym, kolejność komunikatów jest znacząca. W takich scenariuszach przetwarzania grupy pokrewne wiadomości razem jako pojedyncza jednostka: żaden lub wszystkie komunikaty są przetwarzane pomyślnie. Aby zaimplementować takie zachowanie, należy użyć sesji przy użyciu kolejek.  
  
 Aby uzyskać więcej informacji, zobacz [grupowanie komunikatów w kolejce w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Korelowanie komunikatów "żądanie-odpowiedź"  
 Chociaż kolejki są zazwyczaj jednokierunkowe, w niektórych scenariuszach możesz chcieć dopasowania odpowiedzi odebrany na żądanie wysłane wcześniej. Jeśli potrzebujesz takiego korelacji, zaleca się stosowanie własnego nagłówka komunikatu protokołu SOAP, zawierający informacje o korelacji z komunikatu. Zazwyczaj nadawcy dołączenie tego pliku nagłówkowego z komunikatem i odbiornik, podczas przetwarzania komunikatu i odpowiadanie nowy komunikat w kolejce odpowiedź z powrotem dołącza nagłówek komunikatu nadawcy, który zawiera informacje o powiązaniu nadawca może Określ komunikat odpowiedzi, komunikatem żądania.  
  
## <a name="integrating-with-non-wcf-applications"></a>Współdziałanie z aplikacjami innych WCF  
 Użyj `MsmqIntegrationBinding` podczas integrowania usług WCF lub klientów przy użyciu usługi WCF nie lub klientów. Aplikacja WCF nie może być MSMQ aplikacji napisanych z użyciem System.Messaging, modelu COM +, Visual Basic lub C++.  
  
 Korzystając z `MsmqIntegrationBinding`, należy pamiętać o następujących kwestiach:  
  
- Treść wiadomości WCF nie jest taka sama jak treść wiadomości usługi MSMQ. Podczas wysyłania wiadomości WCF przy użyciu Zakolejkowane powiązanie, treść wiadomości WCF znajduje się wewnątrz wiadomości usługi MSMQ. Infrastruktura usługi MSMQ jest oblivious do tych dodatkowych informacji; jego widzi tylko wiadomości usługi MSMQ.  
  
- `MsmqIntegrationBinding` obsługuje serializację popularnych typów. Na podstawie typu serializacji, typ treści komunikatu ogólny, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, przyjmuje parametry innego typu. Na przykład <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> wymaga `MsmqMessage\<byte[]>` i <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> wymaga `MsmqMessage<Stream>`.  
  
- Serializacji XML można określić przy użyciu znanego typu `KnownTypes` atrybutu na [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element, który jest następnie używany do określenia sposobu deserializacji komunikatu XML.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Grupowanie komunikatów z obsługą kolejek w ramach sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)
- [Tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)
- [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Korzystanie z zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)
- [Rozwiązywanie problemów obsługi komunikatów kolejek](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
