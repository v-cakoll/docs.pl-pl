---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 5eae08ab6b8dee5ebece66a1c41c87ebab3387bc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963277"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF

W tym artykule opisano, jak klient może asynchronicznie uzyskać dostęp do operacji usługi. Usługa w tym artykule implementuje interfejs `ICalculator`. Klient może wywoływać operacje w tym interfejsie asynchronicznie przy użyciu opartego na zdarzeniach asynchronicznego modelu wywoływania. (Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [programowanie wielowątkowe ze wzorcem asynchronicznym opartym na zdarzeniach](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)). Aby zapoznać się z przykładem, który pokazuje, jak zaimplementować operację asynchronicznie w usłudze, zobacz [How to: implementowanie asynchronicznej operacji usługi](../how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchroniczny model wywoływania oparty na zdarzeniach nie jest obsługiwany w przypadku używania <xref:System.ServiceModel.ChannelFactory%601>. Aby uzyskać informacje na temat wykonywania wywołań asynchronicznych przy użyciu <xref:System.ServiceModel.ChannelFactory%601>, zobacz [How to: Call operacje asynchronicznie przy użyciu fabryki kanałów](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchronicznie wywoływać operacje usługi WCF  
  
1. Uruchom narzędzie do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z opcjami `/async` i `/tcv:Version35` polecenia, jak pokazano w poniższym poleceniu.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Spowoduje to wygenerowanie, oprócz synchronicznych i standardowych operacji asynchronicznych opartych na delegatach, klasy klienta WCF, która zawiera:  
  
    - Dwie <`operationName`>`Async` operacji do użycia z podejściem wywołań asynchronicznych opartych na zdarzeniach. Na przykład:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Zdarzenia ukończone w formularzu <`operationName`>`Completed` do użycia z podejściem wywołań asynchronicznych opartych na zdarzeniach. Na przykład:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType> typy dla każdej operacji (formularza <`operationName`>`CompletedEventArgs`) do użycia z podejście asynchroniczne wywołań asynchronicznych opartych na zdarzeniach. Na przykład:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. W aplikacji wywołującej Utwórz metodę wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Przed wywołaniem operacji Użyj nowej generycznej <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName`>`EventArgs`, aby dodać metodę obsługi (utworzoną w poprzednim kroku) do <`operationName`>zdarzenia `Completed`. Następnie Wywołaj metodę <`operationName`>`Async`. Na przykład:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
> Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości są zwracane jako właściwość `Result`, a pozostałe są zwracane jako właściwości w obiekcie <xref:System.EventArgs>. Wynikiem tego jest to, że jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, domyślny obiekt <xref:System.EventArgs> zwraca jedną wartość jako właściwość `Result`, a pozostała część to właściwości obiektu <xref:System.EventArgs>. Jeśli chcesz otrzymać obiekt komunikatu jako właściwość `Result` i mieć wartości zwracanych jako właściwości dla tego obiektu, użyj opcji polecenie `/messageContract`. Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako właściwości `Result` w obiekcie <xref:System.EventArgs>. Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: wdrażanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
