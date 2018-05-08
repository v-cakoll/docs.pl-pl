---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 95279f90fbf87d64d96a1ed036449b72416e4f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów
W tym temacie opisano, jak klienta można uzyskać dostępu do operacji usługi asynchronicznie przy użyciu <xref:System.ServiceModel.ChannelFactory%601>-aplikacji klienta. (Przy użyciu <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> obiekt do wywołania usługi można użyć sterowane zdarzeniami asynchroniczne wywołanie modelu. Aby uzyskać więcej informacji, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat oparty na zdarzeniach asynchroniczne wywołanie modelu, zobacz [programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)  
  
 Implementuje usługę w tym temacie `ICalculator` interfejsu. Klienta można wywołać operacji w tym interfejsie asynchronicznie, co oznacza, że operacji, takich jak `Add` są podzielone na dwie metody `BeginAdd` i `EndAdd`, pierwsza z nich inicjuje połączenie i drugie, z których pobiera wynik Po zakończeniu operacji. Przykład pokazujący sposób zaimplementować operację asynchronicznie w usłudze, zobacz [porady: Implementowanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać szczegółowe informacje o operacjach synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchroniczne wywoływanie operacji usługi WCF  
  
1.  Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia z `/async` opcji, jak pokazano w poniższym poleceniu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Powoduje to wersja klienta asynchroniczne kontraktu usługi dla tej operacji.  
  
2.  Utwórz funkcję wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończone, jak pokazano w poniższym kodzie próbki.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  Aby uzyskać dostęp do operacji usługi asynchronicznie, należy utworzyć klienta i wywołania `Begin[Operation]` (na przykład `BeginAdd`) i określ funkcję wywołania zwrotnego, jak pokazano w poniższym kodzie próbki.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Podczas funkcja wywołania zwrotnego, gdy klient wywołuje `End<operation>` (na przykład `EndAdd`) można pobrać wyniku.  
  
## <a name="example"></a>Przykład  
 Implementuje usługę, która jest używana z kodu klienta, który jest używany w poprzedniej procedurze `ICalculator` interfejsu, jak pokazano w poniższym kodzie. Na stronie usługi `Add` i `Subtract` operacji kontraktu są wywoływane synchronicznie przez Windows Communication Foundation (WCF) w czasie wykonywania, nawet jeśli poprzednie kroki klienta są wywoływane asynchronicznie na kliencie. `Multiply` i `Divide` operacje są używane do wywoływania usługi asynchronicznie po stronie usługi nawet wtedy, gdy klient wywołuje ich synchronicznie. W tym przykładzie <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwości `true`. Ustawienie właściwości w połączeniu z implementacją [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wzorca asynchronicznego, określa, że czas uruchomienia do asynchronicznego wywołania operacji.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontraktu usługi: Przykładowe asynchroniczne](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
