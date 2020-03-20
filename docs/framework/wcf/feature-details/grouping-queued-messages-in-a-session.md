---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185158"
---
# <a name="grouping-queued-messages-in-a-session"></a>Grupowanie komunikatów z obsługą kolejek w ramach sesji
Windows Communication Foundation (WCF) udostępnia sesję, która umożliwia grupowanie zestawu powiązanych wiadomości razem do przetwarzania przez jedną aplikację odbierającą. Wiadomości, które są częścią sesji musi być częścią tej samej transakcji. Ponieważ wszystkie wiadomości są częścią tej samej transakcji, jeśli jedna wiadomość nie może być przetworzona, cała sesja zostanie wycofana. Sesje mają podobne zachowania w odniesieniu do kolejek utraconych wiadomości i kolejek trucizny. Właściwość Czas wygaśnięcia (TTL) ustawiona na powiązanie w kolejce skonfigurowane dla sesji jest stosowana do sesji jako całości. Jeśli tylko niektóre wiadomości w sesji są wysyłane przed wygaśnięciem czasu wygaśnięcia, cała sesja jest umieszczana w kolejce utraconych wiadomości. Podobnie, gdy wiadomości w sesji nie mogą być wysyłane do aplikacji z kolejki aplikacji, cała sesja jest umieszczana w kolejce trucić (jeśli są dostępne).  
  
## <a name="message-grouping-example"></a>Przykład grupowania wiadomości  
 Jednym z przykładów, gdzie grupowanie wiadomości jest przydatne jest podczas implementowania aplikacji przetwarzania zamówień jako usługi WCF. Na przykład klient przesyła zamówienie do tej aplikacji, która zawiera wiele elementów. Dla każdego elementu klient wykonuje wywołanie usługi, co powoduje wysłanie osobnej wiadomości. Istnieje możliwość wyświetlania A, aby otrzymać pierwszy element, a serwer B, aby otrzymać drugi element. Za każdym razem, gdy element jest dodawany, serwer przetwarzający ten element musi znaleźć odpowiednią kolejność i dodać do niego element, który jest wysoce nieefektywny. Nadal można napotkać takie nieefektywności tylko z jednego serwera obsługi wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia obecnie przetwarzane i określić, który z nich nowy element należy do. Grupowanie wszystkich żądań dla jednego zamówienia znacznie upraszcza implementację takiej aplikacji. Aplikacja kliencka wysyła wszystkie elementy dla pojedynczego zamówienia w sesji, więc gdy usługa przetwarza zamówienie, przetwarza całą sesję jednocześnie. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Aby skonfigurować umowę serwisową do używania sesji  
  
1. Zdefiniuj umowę serwisową, która wymaga sesji. Zrób to <xref:System.ServiceModel.ServiceContractAttribute> za pomocą atrybutu, określając:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Oznacz operacje w umowie jako jednokierunkowe, ponieważ te metody nie zwracają niczego. Odbywa się to <xref:System.ServiceModel.OperationContractAttribute> za pomocą atrybutu, określając:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Zaimplementuj <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> umowę <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>serwisową i określ wartość . Spowoduje to wystąpienie usługi tylko raz dla każdej sesji.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Każda operacja usługi wymaga transakcji. Określ to <xref:System.ServiceModel.OperationBehaviorAttribute> za pomocą atrybutu. Operacja, która kończy transakcję, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`powinna również być ustawiona na .  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. Skonfiguruj punkt końcowy, który `NetMsmqBinding` używa powiązania dostarczonego przez system.  
  
6. Utwórz kolejkę <xref:System.Messaging>transakcyjną przy użyciu programu . Kolejkę można również utworzyć za pomocą usługi kolejkowania wiadomości (MSMQ) lub programu MMC. Jeśli to zrobisz, utwórz kolejkę transakcyjną.  
  
7. Utwórz hosta usługi dla <xref:System.ServiceModel.ServiceHost>usługi za pomocą programu .  
  
8. Otwórz hosta usługi, aby udostępnić usługę.  
  
9. Zamknij hosta usługi.  
  
#### <a name="to-set-up-a-client"></a>Aby skonfigurować klienta  
  
1. Utwórz zakres transakcji do zapisu w kolejce transakcyjnej.  
  
2. Utwórz klienta WCF za pomocą narzędzia [Narzędzie narzędziowe ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
3. Złóż zamówienie.  
  
4. Zamknij klienta WCF.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kod `IProcessOrder` dla usługi i dla klienta, który używa tej usługi. Pokazuje, jak WCF używa sesji w kolejce, aby zapewnić zachowanie grupowania.  
  
### <a name="code-for-the-service"></a>Kod usługi  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kod dla klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Zobacz też

- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
