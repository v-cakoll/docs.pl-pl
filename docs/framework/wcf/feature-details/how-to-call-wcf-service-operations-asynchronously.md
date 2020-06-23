---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
description: Dowiedz się, jak utworzyć klienta WCF, który może uzyskiwać dostęp do operacji usługi asynchronicznej przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aa31f64473111800f4cd01907a0446c94f368456
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247237"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF

W tym artykule opisano, jak klient może asynchronicznie uzyskać dostęp do operacji usługi. Usługa w tym artykule implementuje `ICalculator` interfejs. Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania. (Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym na zdarzeniach](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)). Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w usłudze, zobacz [How to: implementowanie asynchronicznej operacji usługi](../how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku korzystania z programu <xref:System.ServiceModel.ChannelFactory%601> . Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy użyciu <xref:System.ServiceModel.ChannelFactory%601> , zobacz [How to: Call operacje asynchronicznie przy użyciu fabryki kanałów](how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchronicznie wywoływać operacje usługi WCF  
  
1. Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą obu `/async` `/tcv:Version35` opcji polecenia i, jak pokazano w poniższym poleceniu.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:  
  
    - Dwie <`operationName` > `Async` operacji do użycia z podejściem asynchronicznym wywołującym zdarzenia. Przykład:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Zdarzenia ukończone w formularzu <`operationName` > `Completed` do użycia z podejściem asynchronicznym wywołującym zdarzenia. Przykład:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>typy dla każdej operacji (formularza <`operationName` > `CompletedEventArgs` ) do użycia z podejściem asynchronicznym wywołującym zdarzenia. Przykład:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Przed wywołaniem operacji należy użyć nowego <xref:System.EventHandler%601?displayProperty=nameWithType> typu ogólnego <, `operationName` > `EventArgs` Aby dodać metodę procedury obsługi (utworzoną w poprzednim kroku) do `operationName` > `Completed` zdarzenia <. Następnie Wywołaj `operationName` > `Async` metodę <. Przykład:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
> Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana jako `Result` Właściwość, a pozostałe są zwracane jako właściwości w <xref:System.EventArgs> obiekcie. W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość jako `Result` Właściwość, a reszta jest właściwościami <xref:System.EventArgs> obiektu. Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, użyj `/messageContract` opcji polecenia. Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: wdrażanie asynchronicznej operacji usługi](../how-to-implement-an-asynchronous-service-operation.md)
