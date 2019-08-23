---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964032"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF
W tym temacie opisano, jak klient może asynchronicznie uzyskiwać dostęp do operacji usługi. Usługa w tym temacie implementuje `ICalculator` interfejs. Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania. (Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym](https://go.microsoft.com/fwlink/?LinkId=248184)na zdarzeniach). Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w [usłudze, zobacz How to: Implementowanie asynchronicznej operacji](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)usługi. Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku <xref:System.ServiceModel.ChannelFactory%601>korzystania z programu. Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy [użyciu <xref:System.ServiceModel.ChannelFactory%601>, zobacz How to: Asynchroniczne wywoływanie operacji przy użyciu fabryki](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kanałów.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchronicznie wywoływać operacje usługi WCF  
  
1. Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą obu `/async` opcji poleceń `/tcv:Version35` i, jak pokazano w poniższym poleceniu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:  
  
    - Dwie <`operationName` > operacjidoużyciazpodejściemasynchronicznym`Async` wywołującym zdarzenia. Przykład:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Zdarzenia ukończone w formularzu <`operationName` > `Completed` do użycia z podejściem asynchronicznym wywołującym zdarzenia. Przykład:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>typy dla każdej operacji (formularza <`operationName`>`CompletedEventArgs`) do użycia z podejściem asynchronicznym wywołującym zdarzenia. Na przykład:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Przed wywołaniem operacji <xref:System.EventHandler%601?displayProperty=nameWithType> należy użyć nowego typu ogólnego <`operationName` > `EventArgs` , aby dodać metodę procedury obsługi (utworzoną w poprzednim kroku) do zdarzenia <`operationName`. > `Completed` Następnie Wywołaj metodę`operationName` <> `Async` . Na przykład:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
> Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana `Result` jako właściwość, a pozostałe są zwracane jako właściwości <xref:System.EventArgs> w obiekcie. W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość `Result` jako właściwość, a reszta jest <xref:System.EventArgs> właściwości obiektu. Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, `/messageContract` Użyj opcji polecenia. Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
