---
title: Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: 268f14bc7294a4cbe6f7253dc7f3c71d89985133
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837964"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
Komunikaty w kolejce mogą kończyć się niepowodzeniem. Te nieudane komunikaty są rejestrowane w kolejce utraconych wiadomości. Nieudane dostarczenie może być spowodowane przyczynami, takimi jak awarie sieci, kolejka usunięta, pełna kolejka, niepowodzenie uwierzytelniania lub niepowodzenie dostarczania na czas.  
  
 Wiadomości w kolejce mogą pozostawać w kolejce przez dłuższy czas, jeśli aplikacja do odbioru nie odczytuje ich z kolejki w odpowiednim czasie. Takie zachowanie może być nieodpowiednie dla komunikatów zależnych od czasu. Komunikaty zależne od czasu mają ustawioną właściwość Time to Live (TTL) ustawianą w powiązaniu umieszczonym w kolejce, która wskazuje, jak długo komunikaty mogą znajdować się w kolejce przed ich wygaśnięciem. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Komunikaty mogą być również umieszczane w kolejce utraconych z innych powodów, takich jak przekroczenie limitu przydziału kolejki lub z powodu błędu uwierzytelniania.  
  
 Ogólnie rzecz biorąc, aplikacje zapisują logikę kompensacji do odczytu wiadomości z kolejki utraconych wiadomości i przyczyn niepowodzenia. Logika kompensacji zależy od przyczyny błędu. Na przykład w przypadku niepowodzenia uwierzytelniania można poprawić certyfikat dołączony do wiadomości i ponownie wysłać wiadomość. Jeśli dostarczenie nie powiodło się, ponieważ osiągnięto limit przydziału kolejki docelowej, możesz ponowić próbę dostarczenia w ramach tej metody, aby rozwiązać problem z limitem przydziału.  
  
 Większość systemów kolejkowania ma kolejkę utraconych wiadomości w całej systemie, w której przechowywane są wszystkie komunikaty zakończone niepowodzeniem z tego systemu. Usługa kolejkowania komunikatów (MSMQ) oferuje dwie kolejki utraconych wiadomości w całym systemie: transakcyjna kolejka utraconych wiadomości w całej systemie, która przechowuje komunikaty, które przestaną być dostarczone do kolejki transakcyjnej, oraz nietransakcyjnej kolejki utraconych wiadomości w całej systemie, która przechowuje komunikaty, które przekończyły się niepowodzeniem dostarczania do kolejki nietransakcyjnej. Jeśli dwa klienci wysyłają komunikaty do dwóch różnych usług, w związku z czym różne kolejki w programie WCF współużytkują tę samą usługę MSMQ do wysłania Nie zawsze jest to optymalna. W kilku przypadkach (na przykład) można nie chcieć, aby jeden klient mógł odczytywać komunikaty innego klienta z kolejki utraconych wiadomości. Udostępniona Kolejka utraconych wiadomości wymaga również od klientów przejrzenia kolejki w celu znalezienia wysyłanego komunikatu, co może być niezwykle kosztowne w oparciu o liczbę komunikatów w kolejce utraconych wiadomości. W związku z tym w`NetMsmqBinding`WCF `MsmqIntegrationBinding,` i usługi MSMQ w systemie Windows Vista zapewniają niestandardową kolejkę utraconych wiadomości (nazywaną czasami kolejką utraconych wiadomości specyficzną dla aplikacji).  
  
 Niestandardowa Kolejka utraconych wiadomości zapewnia izolację między klientami, którzy korzystają z tej samej usługi MSMQ do wysyłania wiadomości.  
  
 W systemach [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]funkcja Windows Communication Foundation (WCF) zapewnia kolejkę utraconych wiadomości w całej systemie dla wszystkich aplikacji klienckich umieszczonych w kolejce. W systemie Windows Vista funkcja WCF udostępnia kolejkę utraconych wiadomości dla każdej Kolejkowanej aplikacji klienckiej.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Określanie użycia kolejki utraconych wiadomości  
 Kolejka utraconych wiadomości znajduje się w Menedżerze kolejek aplikacji wysyłającej. Przechowuje komunikaty, które wygasły lub które nie powiodły się.  
  
 Powiązanie ma następujące właściwości kolejki utraconych wiadomości:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Odczytywanie wiadomości z kolejki utraconych wiadomości  
 Aplikacja, która odczytuje komunikaty z kolejki utraconych wiadomości, jest podobna do usługi WCF, która odczytuje z kolejki aplikacji, z wyjątkiem następujących drobnych różnic:  
  
- Aby można było odczytać wiadomości z kolejki utraconych wiadomości transakcyjnych systemu, Uniform Resource Identifier (URI) musi mieć postać: net. MSMQ://localhost/system $;D eadXact.  
  
- Aby można było odczytać wiadomości z nietransakcyjnej kolejki utraconych wiadomości, identyfikator URI musi mieć postać: net. MSMQ://localhost/system $;D eadLetter.  
  
- Aby można było odczytać wiadomości z niestandardowej kolejki utraconych wiadomości, identyfikator URI musi mieć postać: net. MSMQ://localhost/Private/\<*Custom-DLQ-name*> gdzie *Custom-DLQ-Name* to nazwa niestandardowej kolejki utraconych wiadomości.  
  
 Aby uzyskać więcej informacji o sposobie adresowania kolejek, zobacz [punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 Stos WCF w odbiorniku pasuje do adresów, na których nasłuchuje usługa, przy użyciu adresu w wiadomości. Jeśli adresy są zgodne, komunikat jest wysyłany; Jeśli nie, komunikat nie jest wysyłany. Może to spowodować problemy podczas odczytywania z kolejki utraconych wiadomości, ponieważ komunikaty w kolejce utraconych wiadomości są zwykle kierowane do usługi, a nie do usługi kolejki utraconych wiadomości. W związku z tym odczytywanie z kolejki utraconych wiadomości musi spowodować zainstalowanie filtru adresów `ServiceBehavior`, który nakazuje stosowi dopasowanie wszystkich komunikatów w kolejce niezależnie od adresata. W szczególnych przypadkach należy dodać `ServiceBehavior` z parametrem <xref:System.ServiceModel.AddressFilterMode.Any> do usługi odczytującej komunikaty z kolejki utraconych wiadomości.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Obsługa skażonych komunikatów z kolejki utraconych wiadomości  
 Obsługa skażonych komunikatów jest dostępna w przypadku kolejek z utraconymi komunikatami z pewnymi warunkami. Ponieważ nie można tworzyć podkolejek z kolejek systemowych, podczas odczytywania z kolejki utraconych wiadomości systemowych nie można ustawić `ReceiveErrorHandling` na `Move`. Należy pamiętać, że w przypadku odczytywania z niestandardowej kolejki utraconych wiadomości można mieć kolejki podrzędne i dlatego `Move` jest prawidłową dyspozycją dla trującego komunikatu.  
  
 Gdy `ReceiveErrorHandling` jest ustawiona na `Reject`, podczas odczytywania z niestandardowej kolejki utraconych wiadomości, Trująca wiadomość jest umieszczana w kolejce utraconych wiadomości systemowych. W przypadku odczytywania z kolejki utraconych wiadomości systemowych komunikat jest porzucany (przeczyszczany). Odrzucanie z kolejki utraconych wiadomości systemowych w usłudze MSMQ powoduje porzucanie (przeczyszczanie) wiadomości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć kolejkę utraconych wiadomości i jak używać jej do przetwarzania wygasłych komunikatów. Przykład jest oparty na przykładzie w [instrukcje: Wymiana komunikatów umieszczonych w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Poniższy przykład pokazuje, jak napisać kod klienta do usługi przetwarzania zamówień, która używa kolejki utraconych wiadomości dla każdej aplikacji. W przykładzie pokazano również, jak przetwarzać komunikaty z kolejki utraconych wiadomości.  
  
 Poniżej przedstawiono kod dla klienta, który określa kolejkę utraconych wiadomości dla każdej aplikacji.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Poniżej znajduje się kod pliku konfiguracji klienta.  

 Poniżej przedstawiono kod dla komunikatów przetwarzania usługi z kolejki utraconych wiadomości.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Poniżej znajduje się kod pliku konfiguracji usługi kolejki utraconych wiadomości.  

## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
