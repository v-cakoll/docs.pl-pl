---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aba41d707426f29c2bcd626dbbe13d16d9e1b1f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624513"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF
W tym temacie opisano, jak klient może uzyskać dostęp do operacji usługi asynchronicznie. Implementuje usługę, w tym temacie `ICalculator` interfejsu. Klient może asynchroniczne wywoływanie operacji w tym interfejsie przy użyciu oparte na zdarzeniach asynchronicznych wywoływania modelu. (Aby uzyskać więcej informacji na temat oparte na zdarzeniach asynchronicznych wywoływania modelu, zobacz [programowania wielowątkowe, za pomocą wzorca asynchronicznego opartego na zdarzeniach](https://go.microsoft.com/fwlink/?LinkId=248184)). Aby uzyskać przykład przedstawia sposób implementowania operacji asynchronicznie w ramach usługi, zobacz [jak: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Oparte na zdarzeniach asynchronicznych wywoływania modelu nie jest obsługiwane w przypadku korzystania <xref:System.ServiceModel.ChannelFactory%601>. Uzyskać informacji na temat wywołań asynchronicznych za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: Wywoływanie operacji asynchronicznie za pomocą fabryki kanałów](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchroniczne wywoływanie operacji usługi WCF  
  
1. Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie zarówno `/async` i `/tcv:Version35` polecenia Opcje ze sobą, jak pokazano w poniższym poleceniu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Spowoduje to wygenerowanie, oprócz synchroniczne i standardowych opartych na delegacie operacji asynchronicznych, klasa klienta WCF, która zawiera:  
  
    - Dwa <`operationName` > `Async` operacje do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście. Na przykład:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Ukończono operację zdarzenia w postaci <`operationName` > `Completed` do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście. Na przykład:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType> typy dla każdej operacji (w postaci <`operationName`>`CompletedEventArgs`) do użytku z programem oparte na zdarzeniach asynchronicznych wywoływania podejście. Na przykład:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. W aplikacji wywołującej Utwórz metody wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończona, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Przed wywołaniem operacji, korzystają z ogólnego nowe <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` dodać metodę procedury obsługi (utworzonym w poprzednim kroku) do <`operationName` > `Completed` zdarzeń. Następnie wywołaj <`operationName` > `Async` metody. Na przykład:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
>  Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu. Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu `/messageContract` opcja polecenia. Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
