---
title: Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: af9ed7d64a60042297e071262be7610c4d791a51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601351"
---
# <a name="best-practices-for-queued-communication"></a>Najlepsze rozwiązania dotyczące komunikacji z obsługą kolejek
Ten temat zawiera zalecane praktyki komunikacji w kolejce w programie Windows Communication Foundation (WCF). W poniższych sekcjach omówiono zalecane praktyki z perspektywy scenariusza.  
  
## <a name="fast-best-effort-queued-messaging"></a>Szybka, Optymalna obsługa wiadomości w kolejce  
 W przypadku scenariuszy, które wymagają rozdzielenia, że obsługa komunikatów w kolejce zapewnia wysoką wydajność i szybkie przesyłanie komunikatów o wysokiej wydajności z gwarancjami najlepszego wysiłku, użyj kolejki nietransakcyjnej i ustaw <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> Właściwość na `false` .  
  
 Ponadto możesz zrezygnować z ponoszenia kosztów zapisu na dysku przez ustawienie <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> właściwości na `false` .  
  
 Zabezpieczenia mają wpływ na wydajność. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności](performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Niezawodna kompleksowa obsługa komunikatów w kolejce  
 W poniższych sekcjach opisano zalecane praktyki dotyczące scenariuszy, które wymagają kompleksowej niezawodnej obsługi komunikatów.  
  
### <a name="basic-reliable-transfer"></a>Podstawowy niezawodny transfer  
 Aby zapewnić kompleksową niezawodność, należy ustawić <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> Właściwość na, aby `true` upewnić się, że transfer. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A>Właściwość może być ustawiona na wartość `true` lub `false` w zależności od wymagań (wartość domyślna to `true` ). Ogólnie rzecz biorąc <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Właściwość jest ustawiana `true` jako część kompleksowej niezawodności. Kompromisem jest koszt wydajności, ale zapewnia trwały komunikat, dzięki czemu komunikat nie zostanie utracony w przypadku awarii Menedżera kolejki.  
  
### <a name="use-of-transactions"></a>Korzystanie z transakcji  
 Aby zapewnić kompleksową niezawodność, należy użyć transakcji. `ExactlyOnce`Gwarancja gwarantuje, że komunikaty są dostarczane do kolejki docelowej. Aby upewnić się, że wiadomość zostanie odebrana, użyj transakcji. Bez transakcji, jeśli usługa ulegnie awarii, utracisz komunikat, który jest dostarczany, ale faktycznie dostarczany do aplikacji.  
  
### <a name="use-of-dead-letter-queues"></a>Korzystanie z kolejek z utraconymi wiadomościami  
 Kolejki utraconych wiadomości upewnij się, że otrzymasz powiadomienie o niepowodzeniu dostarczenia komunikatu do kolejki docelowej. Można użyć kolejki utraconych wiadomości dostarczonych przez system lub niestandardowej kolejki utraconych wiadomości. Ogólnie rzecz biorąc, używanie niestandardowej kolejki utraconych wiadomości jest najlepszym rozwiązaniem, ponieważ umożliwia wysyłanie wiadomości utraconych z jednej aplikacji do pojedynczej kolejki utraconych wiadomości. W przeciwnym razie wszystkie wiadomości utracone, które wystąpiły dla wszystkich aplikacji uruchomionych w systemie, są dostarczane do pojedynczej kolejki. Każda aplikacja musi następnie przeszukać kolejkę utraconych wiadomości, aby znaleźć komunikaty utraconych danych, które są istotne dla danej aplikacji. Czasami użycie niestandardowej kolejki utraconych wiadomości nie jest możliwe, na przykład w przypadku korzystania z usługi MSMQ 3,0.  
  
 Nie zaleca się wyłączania kolejek z utraconymi wiadomościami w celu zapewnienia komunikacji niezawodnej.  
  
 Aby uzyskać więcej informacji, zobacz [Korzystanie z kolejek utraconych w celu obsługi niepowodzeń transferu komunikatów](using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Korzystanie z obsługi komunikatów trujących  
 Obsługa komunikatów trujących zapewnia możliwość odzyskania sprawności po niepowodzeniu przetwarzania komunikatów.  
  
 W przypadku korzystania z funkcji Trująca obsługa komunikatów upewnij się, że <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> Właściwość ma ustawioną odpowiednią wartość. Ustawienie to <xref:System.ServiceModel.ReceiveErrorHandling.Drop> oznacza, że dane zostaną utracone. Z drugiej strony, ustawiając ją na <xref:System.ServiceModel.ReceiveErrorHandling.Fault> Błędy hosta usługi, gdy wykryje trujący komunikat. W przypadku korzystania z usługi MSMQ 3,0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> najlepszym rozwiązaniem jest uniknięcie utraty danych i przeniesienie skażonego komunikatu z metody. <xref:System.ServiceModel.ReceiveErrorHandling.Move>Zalecanym podejściem jest użycie usługi MSMQ 4,0. <xref:System.ServiceModel.ReceiveErrorHandling.Move>przenosi trującą wiadomość z kolejki, aby usługa mogła nadal przetwarzać nowe komunikaty. Nieskażony komunikat może następnie przetworzyć trujący komunikat osobno.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa skażonych komunikatów](poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Osiągnięcie dużej przepływności  
 Aby osiągnąć wysoką przepływność w jednym punkcie końcowym, użyj następujących:  
  
- Przetwarzanie wsadowe transakcyjne. Transakcyjna Partia zadań zapewnia, że wiele komunikatów może być odczytywanych w jednej transakcji. Umożliwia to optymalizację zatwierdzeń transakcji, co zwiększa ogólną wydajność. Koszt przetwarzania wsadowego polega na tym, że jeśli wystąpi błąd w pojedynczym komunikacie w ramach partii, cała partia zostanie wycofana, a komunikaty muszą być przetwarzane pojedynczo do momentu, aż będzie można bezpiecznie wykonać operację wsadową. W większości przypadków trujące komunikaty są rzadkie, więc przetwarzanie wsadowe jest preferowanym sposobem zwiększenia wydajności systemu, szczególnie w przypadku innych menedżerów zasobów, które uczestniczą w transakcji. Aby uzyskać więcej informacji, zobacz Tworzenie [wsadowe komunikatów w transakcji](batching-messages-in-a-transaction.md).  
  
- Współbieżności. Współbieżność zwiększa przepływność, ale współbieżność wpływa również na rywalizację o zasoby udostępnione. Aby uzyskać więcej informacji, zobacz [concurrency](../samples/concurrency.md).  
  
- Ograniczania. W celu uzyskania optymalnej wydajności Ogranicz liczbę komunikatów w potoku dyspozytora. Aby zapoznać się z przykładem, jak to zrobić, zobacz [ograniczanie](../samples/throttling.md).  
  
 Podczas korzystania z usługi Batch należy pamiętać, że współbieżność i ograniczanie przepustowości są tłumaczone na współbieżne partie.  
  
 Aby osiągnąć wyższą przepływność i dostępność, użyj farmy usług WCF odczytanych z kolejki. Wymaga to, aby wszystkie te usługi uwidaczniali ten sam kontrakt w tym samym punkcie końcowym. Podejście farmy działa najlepiej w przypadku aplikacji, które mają wysoką szybkość produkcyjną komunikatów, ponieważ umożliwia ona wszystkim usługom odczytywanie z tej samej kolejki.  
  
 W przypadku korzystania z Farm należy pamiętać, że usługa MSMQ 3,0 nie obsługuje zdalnych operacji odczytu. Usługa MSMQ 4,0 obsługuje zdalne odczyty transakcyjne.  
  
 Aby uzyskać więcej informacji, zobacz Tworzenie [wsadowe komunikatów w transakcji](batching-messages-in-a-transaction.md) i [różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Kolejkowanie przy użyciu semantyki jednostki pracy  
 W niektórych scenariuszach Grupa komunikatów w kolejce może być powiązana i dlatego kolejność tych komunikatów jest istotna. W takich scenariuszach przetwarzanie grupy powiązanych komunikatów odbywa się wraz z pojedynczą jednostką: wszystkie komunikaty są przetwarzane pomyślnie lub nie są. Aby zaimplementować takie zachowanie, użyj sesji z kolejkami.  
  
 Aby uzyskać więcej informacji, zobacz [grupowanie komunikatów umieszczonych w kolejce w sesji](grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Skorelowanie komunikatów z odpowiedzią na żądanie  
 Chociaż kolejki są zwykle jednokierunkowe, w niektórych scenariuszach może być konieczne skorelowanie odpowiedzi odebranej wcześniej wysłanego żądania. Jeśli wymagana jest taka korelacja, zaleca się zastosowanie własnego nagłówka komunikatu protokołu SOAP zawierającego informacje o korelacji z wiadomością. Zazwyczaj nadawca dołącza ten nagłówek wraz z wiadomością i odbiorcę, po przetworzeniu komunikatu i odpowiedzeniu z powrotem przy użyciu nowej wiadomości w kolejce odpowiedzi dołącza nagłówek komunikatu nadawcy, który zawiera informacje o korelacji, dzięki czemu nadawca może zidentyfikować komunikat odpowiedzi z żądaniem.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integrowanie z aplikacjami nieobsługującymi usług WCF  
 Służy `MsmqIntegrationBinding` do integrowania usług lub klientów programu WCF z usługami lub klientami spoza środowiska WCF. Aplikacja nieobsługująca programu WCF może być aplikacją usługi MSMQ zapisaną przy użyciu funkcji system. Messaging, COM+, Visual Basic lub C++.  
  
 Korzystając z programu `MsmqIntegrationBinding` , należy pamiętać o następujących kwestiach:  
  
- Treść komunikatu WCF nie jest taka sama jak treść wiadomości MSMQ. Podczas wysyłania komunikatu WCF przy użyciu podanego w kolejce powiązania treść komunikatu WCF jest umieszczana w komunikacie usługi MSMQ. Infrastruktura usługi MSMQ jest Oblivious do tych dodatkowych informacji; widzi tylko komunikat usługi MSMQ.  
  
- `MsmqIntegrationBinding`obsługuje popularne typy serializacji. W oparciu o typ serializacji, typ treści komunikatu ogólnego, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> ma inne parametry typu. Na przykład <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> wymaga `MsmqMessage\<byte[]>` i <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> wymaga `MsmqMessage<Stream>` .  
  
- Przy użyciu serializacji XML można określić typ znany przy użyciu `KnownTypes` atrybutu [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu, który jest następnie używany do określenia sposobu deserializacji wiadomości XML.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie kolejek w programie WCF](queuing-in-wcf.md)
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Grupowanie komunikatów z obsługą kolejek w ramach sesji](grouping-queued-messages-in-a-session.md)
- [Tworzenie partii komunikatów w ramach transakcji](batching-messages-in-a-transaction.md)
- [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Obsługa komunikatów zanieczyszczonych](poison-message-handling.md)
- [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Ochrona komunikatów za pomocą zabezpieczeń transportu](securing-messages-using-transport-security.md)
- [Korzystanie z zabezpieczeń komunikatów](securing-messages-using-message-security.md)
- [Rozwiązywanie problemów obsługi komunikatów kolejek](troubleshooting-queued-messaging.md)
