---
title: "Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f8f1419deb60b1f68e47c26c0edd5523a9d23768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Instrukcje: Asynchroniczne wywoływanie operacji usługi WCF
W tym temacie opisano, jak klient ma dostęp do operacji usługi asynchronicznie. Implementuje usługę w tym temacie `ICalculator` interfejsu. Klienta można wywołać operacji w tym interfejsie asynchronicznie przy użyciu sterowane zdarzeniami asynchroniczne wywołanie modelu. (Aby uzyskać więcej informacji na temat oparty na zdarzeniach asynchroniczne wywołanie modelu, zobacz [programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](http://go.microsoft.com/fwlink/?LinkId=248184)). Przykład pokazujący sposób wykonania operacji asynchronicznie w usłudze, zobacz [porady: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Sterowane zdarzeniami asynchroniczne wywołanie modelu nie jest obsługiwany przy użyciu <xref:System.ServiceModel.ChannelFactory%601>. Informacji o wprowadzaniu wywołania asynchroniczne przy użyciu <xref:System.ServiceModel.ChannelFactory%601>, zobacz [porady: wywołanie operacji asynchronicznie przy użyciu fabryki kanałów](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchroniczne wywoływanie operacji usługi WCF  
  
1.  Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie zarówno `/async` i `/tcv:Version35` razem polecenie Opcje, jak pokazano w poniższym poleceniu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Spowoduje to wygenerowanie, oprócz synchroniczne i standardowe na podstawie delegata operacji asynchronicznych, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta, który zawiera:  
  
    -   Dwa <`operationName` > `Async` operacji do użycia z oparty na zdarzeniach asynchroniczne wywołanie podejściem. Na przykład:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Zakończono operację zdarzenia w postaci <`operationName` > `Completed` do użytku z oparty na zdarzeniach asynchroniczne wywołanie podejściem. Na przykład:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType>typy dla każdej operacji (w postaci <`operationName`>`CompletedEventArgs`) z opartego na zdarzeniach asynchroniczne wywołanie podejście do użytku. Na przykład:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  W aplikacji wywołującej Utwórz metody wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończone, jak pokazano w poniższym kodzie próbki.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Przed wywołaniem operacji, należy użyć nowego ogólny <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` dodać metoda obsługi (utworzonego w poprzednim kroku) do <`operationName` > `Completed` zdarzeń. Następnie wywołaj <`operationName` > `Async` metody. Na przykład:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
>  Wskazówek dotyczących modelu asynchroniczny oparty na zdarzeniach stanu, że jeśli zostanie zwrócony więcej niż jedną wartość, jedna wartość jest zwracana jako `Result` właściwości, a inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadanych za pomocą opcji polecenia asynchroniczny oparty na zdarzeniach i operacji zwraca więcej niż jedną wartość, domyślna <xref:System.EventArgs> obiektu zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu. Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mieć zwracanych wartości jako właściwości tego obiektu, użyj `/messageContract` — opcja polecenia. Spowoduje to wygenerowanie podpisie, który zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzny zwracanych wartości są następnie właściwości obiektu komunikatu odpowiedzi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
