---
title: 'Instrukcje: asynchroniczne wywoływanie operacji za pomocą fabryki kanałów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: adc4d519e8d29fef5595ab7ddc3168462525c4e2
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895235"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Instrukcje: asynchroniczne wywoływanie operacji za pomocą fabryki kanałów
W tym temacie opisano, w jaki sposób klient może uzyskiwać dostęp do operacji usługi <xref:System.ServiceModel.ChannelFactory%601>asynchronicznej podczas korzystania z aplikacji klienckiej opartej na. (W przypadku używania <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> obiektu do wywoływania usługi można użyć opartego na zdarzeniach asynchronicznego modelu wywoływania. Aby uzyskać więcej informacji, zobacz [jak: Asynchroniczne](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)wywoływanie operacji usługi. Aby uzyskać więcej informacji o asynchronicznym modelu wywoływania opartych na zdarzeniach, zobacz [asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
 Usługa w tym temacie implementuje `ICalculator` interfejs. Klient może wywoływać operacje w tym interfejsie asynchronicznie, co oznacza, że `Add` operacje takie jak są podzielone na `BeginAdd` dwie `EndAdd`metody, a pierwsza, która inicjuje wywołanie, a drugie, które pobiera wynik. Po zakończeniu operacji. Przykład przedstawiający sposób asynchronicznego implementowania operacji w usłudze można znaleźć w temacie [How to: Implementowanie asynchronicznej operacji](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)usługi. Aby uzyskać szczegółowe informacje na temat operacji synchronicznych i asynchronicznych, zobacz [Operacje synchroniczne i asynchroniczne](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchronicznie wywoływać operacje usługi WCF  
  
1. Uruchom narzędzie narzędzia [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/async` opcją, jak pokazano w poniższym poleceniu.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Spowoduje to wygenerowanie asynchronicznej wersji klienta kontraktu usługi dla operacji.  
  
2. Utwórz funkcję wywołania zwrotnego, która ma być wywoływana po zakończeniu operacji asynchronicznej, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Aby uzyskać dostęp do operacji usługi asynchronicznej, Utwórz klienta i Wywołaj `Begin[Operation]` (na `BeginAdd`przykład) i określ funkcję wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Gdy funkcja wywołania zwrotnego jest wykonywana, klient `End<operation>` wywołuje (na `EndAdd`przykład), aby pobrać wynik.  
  
## <a name="example"></a>Przykład  
 Usługa, która jest używana z kodem klienta używanym w poprzedniej procedurze, implementuje `ICalculator` interfejs, jak pokazano w poniższym kodzie. Po stronie `Add` usługi i `Subtract` operacje kontraktu są wywoływane synchronicznie przez czas wykonywania Windows Communication Foundation (WCF), mimo że poprzednia procedura klienta jest wywoływana asynchronicznie na kliencie. Operacje `Multiply` i`Divide` są używane do wywołania usługi asynchronicznie po stronie usługi, nawet jeśli klient wywołuje je synchronicznie. Ten przykład ustawia <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwość na `true`. To ustawienie właściwości, w połączeniu z implementacją wzorca asynchronicznego .NET Framework, informuje czas wykonywania, aby wywołać operację asynchronicznie.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
