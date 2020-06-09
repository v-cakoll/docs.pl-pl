---
title: Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: f07397b4c10ffec4902dbde37b622978d00f5b63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594988"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
Komunikaty w kolejce mogą kończyć się niepowodzeniem. Te nieudane komunikaty są rejestrowane w kolejce utraconych wiadomości. Nieudane dostarczenie może być spowodowane przyczynami, takimi jak awarie sieci, kolejka usunięta, pełna kolejka, niepowodzenie uwierzytelniania lub niepowodzenie dostarczania na czas.  
  
 Wiadomości w kolejce mogą pozostawać w kolejce przez dłuższy czas, jeśli aplikacja do odbioru nie odczytuje ich z kolejki w odpowiednim czasie. Takie zachowanie może być nieodpowiednie dla komunikatów zależnych od czasu. Komunikaty zależne od czasu mają ustawioną właściwość Time to Live (TTL) ustawianą w powiązaniu umieszczonym w kolejce, która wskazuje, jak długo komunikaty mogą znajdować się w kolejce przed ich wygaśnięciem. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Komunikaty mogą być również umieszczane w kolejce utraconych z innych powodów, takich jak przekroczenie limitu przydziału kolejki lub z powodu błędu uwierzytelniania.  
  
 Ogólnie rzecz biorąc, aplikacje zapisują logikę kompensacji do odczytu wiadomości z kolejki utraconych wiadomości i przyczyn niepowodzenia. Logika kompensacji zależy od przyczyny błędu. Na przykład w przypadku niepowodzenia uwierzytelniania można poprawić certyfikat dołączony do wiadomości i ponownie wysłać wiadomość. Jeśli dostarczenie nie powiodło się, ponieważ osiągnięto limit przydziału kolejki docelowej, możesz ponowić próbę dostarczenia w ramach tej metody, aby rozwiązać problem z limitem przydziału.  
  
 Większość systemów kolejkowania ma kolejkę utraconych wiadomości w całej systemie, w której przechowywane są wszystkie komunikaty zakończone niepowodzeniem z tego systemu. Usługa kolejkowania komunikatów (MSMQ) oferuje dwie kolejki utraconych wiadomości w całej sieci: transakcyjną kolejkę utraconych systemów, która przechowuje komunikaty, które przestaną być dostarczone do kolejki transakcyjnej, oraz nietransakcyjnej kolejki utraconych wiadomości w całej systemie, która przechowuje komunikaty, których dostarczenie nie powiodło się w kolejce nietransakcyjnej. Jeśli dwa klienci wysyłają komunikaty do dwóch różnych usług, w związku z czym różne kolejki w programie WCF współużytkują tę samą usługę MSMQ do wysłania Nie zawsze jest to optymalna. W kilku przypadkach (na przykład) można nie chcieć, aby jeden klient mógł odczytywać komunikaty innego klienta z kolejki utraconych wiadomości. Udostępniona Kolejka utraconych wiadomości wymaga również od klientów przejrzenia kolejki w celu znalezienia wysyłanego komunikatu, co może być niezwykle kosztowne w oparciu o liczbę komunikatów w kolejce utraconych wiadomości. W związku z tym w programie WCF `NetMsmqBinding` `MsmqIntegrationBinding,` i usługi MSMQ w systemie Windows Vista zapewniają niestandardową kolejkę utraconych wiadomości (nazywaną czasami kolejką utraconych wiadomości specyficzną dla aplikacji).  
  
 Niestandardowa Kolejka utraconych wiadomości zapewnia izolację między klientami, którzy korzystają z tej samej usługi MSMQ do wysyłania wiadomości.  
  
 W systemach Windows Server 2003 i Windows XP Windows Communication Foundation (WCF) zapewnia kolejkę utraconych wiadomości w całej systemie dla wszystkich aplikacji klienckich umieszczonych w kolejce. W systemie Windows Vista funkcja WCF udostępnia kolejkę utraconych wiadomości dla każdej Kolejkowanej aplikacji klienckiej.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Określanie użycia kolejki utraconych wiadomości  
 Kolejka utraconych wiadomości znajduje się w Menedżerze kolejek aplikacji wysyłającej. Przechowuje komunikaty, które wygasły lub które nie powiodły się.  
  
 Powiązanie ma następujące właściwości kolejki utraconych wiadomości:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Odczytywanie wiadomości z kolejki utraconych wiadomości  
 Aplikacja, która odczytuje komunikaty z kolejki utraconych wiadomości, jest podobna do usługi WCF, która odczytuje z kolejki aplikacji, z wyjątkiem następujących drobnych różnic:  
  
- Aby można było odczytać wiadomości z kolejki utraconych wiadomości transakcyjnych systemu, Uniform Resource Identifier (URI) musi mieć postać: net. MSMQ://localhost/system $;D eadXact.  
  
- Aby można było odczytać wiadomości z nietransakcyjnej kolejki utraconych wiadomości, identyfikator URI musi mieć postać: net. MSMQ://localhost/system $;D eadLetter.  
  
- Aby odczytać wiadomości z niestandardowej kolejki utraconych wiadomości, identyfikator URI musi mieć postać: net. MSMQ://localhost/Private/, \<*custom-dlq-name*> gdzie *Custom-DLQ-Name* to nazwa niestandardowej kolejki utraconych wiadomości.  
  
 Aby uzyskać więcej informacji o sposobie adresowania kolejek, zobacz [punkty końcowe usługi i adresowanie kolejki](service-endpoints-and-queue-addressing.md).  
  
 Stos WCF w odbiorniku pasuje do adresów, na których nasłuchuje usługa, przy użyciu adresu w wiadomości. Jeśli adresy są zgodne, komunikat jest wysyłany; Jeśli nie, komunikat nie jest wysyłany. Może to spowodować problemy podczas odczytywania z kolejki utraconych wiadomości, ponieważ komunikaty w kolejce utraconych wiadomości są zwykle kierowane do usługi, a nie do usługi kolejki utraconych wiadomości. W związku z tym odczytywanie z kolejki utraconych wiadomości musi instalować filtr adresów `ServiceBehavior` , który nakazuje stosowi dopasowanie wszystkich komunikatów w kolejce niezależnie od adresata. W każdym przypadku należy dodać `ServiceBehavior` z <xref:System.ServiceModel.AddressFilterMode.Any> parametrem do usługi odczytywania komunikatów z kolejki utraconych wiadomości.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Obsługa skażonych komunikatów z kolejki utraconych wiadomości  
 Obsługa skażonych komunikatów jest dostępna w przypadku kolejek z utraconymi komunikatami z pewnymi warunkami. Ponieważ nie można tworzyć podkolejek z kolejek systemowych, podczas odczytywania z kolejki utraconych wiadomości systemowych `ReceiveErrorHandling` nie można ustawić wartości `Move` . Należy pamiętać, że jeśli czytasz z niestandardowej kolejki utraconych wiadomości, możesz mieć kolejki podrzędne i, w związku z tym, `Move` jest prawidłową dyspozycją dla trującej wiadomości.  
  
 Gdy `ReceiveErrorHandling` jest ustawiona na `Reject` , podczas odczytywania z niestandardowej kolejki utraconych wiadomości, Trująca wiadomość jest umieszczana w kolejce utraconych wiadomości systemowych. W przypadku odczytywania z kolejki utraconych wiadomości systemowych komunikat jest porzucany (przeczyszczany). Odrzucanie z kolejki utraconych wiadomości systemowych w usłudze MSMQ powoduje porzucanie (przeczyszczanie) wiadomości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć kolejkę utraconych wiadomości i jak używać jej do przetwarzania wygasłych komunikatów. Przykład jest oparty na przykładzie w [instrukcje: Wymiana komunikatów umieszczonych w kolejce z punktami końcowymi WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md). Poniższy przykład pokazuje, jak napisać kod klienta do usługi przetwarzania zamówień, która używa kolejki utraconych wiadomości dla każdej aplikacji. W przykładzie pokazano również, jak przetwarzać komunikaty z kolejki utraconych wiadomości.  
  
 Poniżej przedstawiono kod dla klienta, który określa kolejkę utraconych wiadomości dla każdej aplikacji.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Poniżej znajduje się kod pliku konfiguracji klienta.  

 Poniżej przedstawiono kod dla komunikatów przetwarzania usługi z kolejki utraconych wiadomości.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Poniżej znajduje się kod pliku konfiguracji usługi kolejki utraconych wiadomości.  

## <a name="see-also"></a>Zobacz też

- [Omówienie kolejek](queues-overview.md)
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Obsługa komunikatów zanieczyszczonych](poison-message-handling.md)
