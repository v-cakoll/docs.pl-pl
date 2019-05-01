---
title: Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: 2f15bf569da6127d6c9d27be255590ce3784d7a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050704"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
Wiadomości w kolejce może zakończyć się niepowodzeniem dostarczania. Te komunikaty zakończone niepowodzeniem są rejestrowane w kolejce wiadomości utraconych. Dostarczanie nie powiodło się, może być spowodowany powodów, takich jak awarie sieci, usunięto kolejkę, pełną kolejkę, wystąpił błąd uwierzytelniania lub niepowodzenie dostarczać oprogramowanie na czas.  
  
 Wiadomości w kolejce może pozostawać w kolejce przez długi czas, jeśli aplikacja odbierająca nie odczytać ich z kolejki w odpowiednim czasie. To zachowanie może nie być odpowiednie dla wiadomości zależne od czasu. Komunikaty zależne od czasu ma czas wygaśnięcia (TTL) właściwością w powiązaniu umieszczonych w kolejce, który wskazuje, jak długo komunikaty mogą znajdować się w kolejce przed wygaśnięciem. Wygasłe komunikaty są wysyłane do specjalnych kolejki o nazwie kolejki utraconych wiadomości. Wiadomości możesz także umieścić w kolejce wiadomości utraconych z innych przyczyn, takich jak przekroczenia przydziału kolejki lub z powodu błędu uwierzytelniania.  
  
 Ogólnie rzecz biorąc aplikacje zapisywać logiki wyrównującej odczytywanie komunikatów z kolejki utraconych wiadomości i przyczyny niepowodzenia. Logiki wyrównującej zależy od przyczynę błędu. Na przykład w przypadku niepowodzenia uwierzytelniania można poprawić certyfikatu załączonego z komunikatem i Wyślij ponownie wiadomość. Jeśli dostarczenie nie powiodło się, ponieważ osiągnięto limit przydziału kolejki docelowej, można ponownie dostarczania w nadziei, że przydział problem został rozwiązany.  
  
 Najbardziej kolejkowania systemy mają kolejki wiadomości utraconych całego systemu, gdzie są przechowywane wszystkie wiadomości nie powiodło się z tego systemu. Usługi kolejkowania komunikatów (MSMQ) udostępnia dwie kolejki utraconych wiadomości systemowe: transakcyjne kolejki wiadomości utraconych całego systemu, przechowujący wiadomości, które nie powiodło się metodę dostarczania nietransakcyjnej kolejki wiadomości utraconych całego systemu, który przechowuje, jak i kolejka transakcyjna wiadomości, które nie powiodło się dostarczania do kolejki nietransakcyjnej. Jeśli dwóch klientów są wysyłanie komunikatów do dwóch różnych usług, a w związku z tym innej kolejki programu WCF udostępniania tej samej usługi MSMQ do wysłania, następnie jest możliwość mają różne komunikaty w kolejce wiadomości utraconych systemu. Nie zawsze jest to optymalne. W kilku przypadkach (na przykład zabezpieczenia) może nie chcieć jednego klienta, aby odczytać innego klienta wiadomości z kolejki utraconych wiadomości. Udostępnione kolejki utraconych wiadomości wymaga także klientów przejrzeć Znajdź komunikat, który one wysyłane, który może być niezwykle kosztowne na podstawie liczby komunikatów w kolejce utraconych wiadomości w kolejce. W związku z tym, w programie WCF`NetMsmqBinding`, `MsmqIntegrationBinding,` i usługi MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] zapewniają niestandardowe kolejki utraconych wiadomości (czasami określane jako kolejki utraconych wiadomości specyficzne dla aplikacji).  
  
 Niestandardowe kolejki utraconych wiadomości zapewnia izolację między klientami, które współużytkują tę samą usługę MSMQ do wysyłania wiadomości.  
  
 Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], Windows Communication Foundation (WCF) zapewnia kolejki wiadomości utraconych systemowe dla wszystkich aplikacji klienckich umieszczonych w kolejce. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], WCF zapewnia kolejki utraconych wiadomości dla każdej aplikacji klienta umieszczonych w kolejce.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Określanie użytkowania kolejki utraconych wiadomości  
 Kolejka utraconych wiadomości jest Menedżer kolejki wysyłania aplikacji. Przechowuje komunikaty wygasły lub powiodły transferu lub dostarczania.  
  
 Powiązanie ma następujące właściwości kolejki utraconych wiadomości:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Odczytywanie komunikatów z kolejki utraconych wiadomości  
 Aplikacja, która odczytuje komunikaty z kolejki utraconych wiadomości jest podobny do usługi WCF, która odczytuje z kolejki usługi aplikacji, z wyjątkiem następujących niewielkich różnic:  
  
- Odczytywanie komunikatów z kolejki utraconych wiadomości transakcyjnych systemu, jednolity identyfikator zasobów (URI) musi mieć postać: net.msmq://localhost/system$; DeadXact.  
  
- Odczytywanie komunikatów z kolejki utraconych wiadomości nietransakcyjnej systemu, identyfikator URI musi mieć postać: net.msmq://localhost/system$; utraconych wiadomości.  
  
- Odczytywanie komunikatów z kolejki utraconych wiadomości niestandardowych, identyfikator URI musi być formularza: net.msmq://localhost/private/\<*niestandardowe dlq nazwy*> gdzie *niestandardowe dlq nazwy* jest nazwa niestandardowa Kolejka utraconych wiadomości.  
  
 Aby uzyskać więcej informacji na temat kolejek adres zobacz [punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 Stos WCF odbiornika dopasowuje adresów, które usługa nasłuchuje na adres w komunikacie. Jeśli adresy są zgodne, jest wysyłany komunikat; w przeciwnym razie nie wysłaniu wiadomości. Może to spowodować problemy podczas czytania z kolejki utraconych wiadomości, ponieważ komunikaty w kolejce wiadomości utraconych zwykle są wysyłane do usługi i nie usługę kolejki utraconych wiadomości. W związku z tym, Usługa odczytu z kolejki utraconych wiadomości, należy zainstalować filtr adresów `ServiceBehavior` , powoduje, że stos, aby dopasować wszystkie komunikaty w kolejce, niezależnie od adresata. W szczególności należy dodać `ServiceBehavior` z <xref:System.ServiceModel.AddressFilterMode.Any> parametru, aby usługa odczytującego komunikaty z kolejki utraconych wiadomości.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Obsługa zanieczyszczonych komunikatów z kolejki utraconych wiadomości  
 Zarządzanie skażonymi komunikatami, obsługa jest dostępna w kolejki utraconych wiadomości, za pomocą niektóre warunki. Ponieważ nie można utworzyć kolejki podrzędnej z kolejek systemu podczas czytania z kolejki utraconych wiadomości systemu `ReceiveErrorHandling` nie można ustawić `Move`. Należy pamiętać, że podczas czytania z kolejki utraconych wiadomości niestandardowych, może mieć kolejki podrzędnej, a więc `Move` jest prawidłowy dyspozycji skażone wiadomości.  
  
 Gdy `ReceiveErrorHandling` ustawiono `Reject`podczas czytania z kolejki utraconych komunikatów, zarządzanie skażonymi komunikatami jest umieszczany w kolejce wiadomości utraconych systemu. Odczytywanie z kolejki utraconych wiadomości systemu, komunikat jest odrzucany (usunięty). Odrzuć z kolejki utraconych wiadomości systemu w usłudze MSMQ spadnie (Przeczyszcza) wiadomości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można utworzyć kolejki utraconych wiadomości oraz sposób jej używać do przetwarzania wygasłe wiadomości. Przykład jest oparty na przykład w [jak: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Poniższy przykład pokazuje, jak napisać kod klienta do kolejności przetwarzania usługi korzystającej z kolejki utraconych wiadomości dla każdej aplikacji. W przykładzie pokazano również sposób przetwarzania komunikatów z kolejki utraconych wiadomości.  
  
 Poniżej przedstawiono kod klienta, który określa kolejki utraconych wiadomości dla każdej aplikacji.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Poniżej znajduje się kod w pliku konfiguracji klienta.  

 Poniżej przedstawiono kod usługi, przetwarzanie komunikatów z kolejki utraconych wiadomości.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Poniżej znajduje się kod w pliku konfiguracji usługi kolejki utraconych wiadomości.  

## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
