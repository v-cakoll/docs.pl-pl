---
title: 'Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 292fd92ebab9d1af2a2623ab55c3324fab2a69dc
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752355"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Instrukcje: Asynchroniczne wywoływanie operacji za pomocą fabryki kanałów
W tym temacie opisano, jak klient może uzyskać dostęp do operacji usługi asynchronicznie podczas korzystania <xref:System.ServiceModel.ChannelFactory%601>— na podstawie aplikacji klienckiej. (Korzystając z <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> obiektu, aby wywołać usługę, można użyć oparte na zdarzeniach asynchronicznych wywoływania modelu. Aby uzyskać więcej informacji, zobacz [porady: wywoływanie operacji usługi asynchronicznie](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat oparte na zdarzeniach asynchronicznych wywoływania modelu, zobacz [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Implementuje usługę, w tym temacie `ICalculator` interfejsu. Klient może asynchroniczne wywoływanie operacji w tym interfejsie, co oznacza, że operacje, takie jak `Add` są podzielone na dwie metody `BeginAdd` i `EndAdd`, pierwsza z nich inicjuje wywołanie i drugim z nich pobiera wyniki Po zakończeniu operacji. Przykład przedstawiający sposób implementowania operacji asynchronicznie w ramach usługi, zobacz [porady: Wdrażanie asynchronicznej operacji usługi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Aby uzyskać szczegółowe informacje o operacje synchroniczne i asynchroniczne, zobacz [synchroniczne i asynchroniczne operacje](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Aby asynchroniczne wywoływanie operacji usługi WCF  
  
1.  Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia z `/async` opcji, jak pokazano w poniższym poleceniu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Spowoduje to wygenerowanie klienta asynchroniczną wersję kontraktu usługi dla tej operacji.  
  
2.  Utwórz funkcję wywołania zwrotnego wywoływana, gdy operacja asynchroniczna jest zakończona, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  Aby uzyskać dostęp do operacji usługi asynchronicznie, należy utworzyć klienta i wywołania `Begin[Operation]` (na przykład `BeginAdd`) i określić funkcję wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Podczas wykonywania funkcji wywołania zwrotnego, gdy klient wywołuje `End<operation>` (na przykład `EndAdd`) można pobrać wyniku.  
  
## <a name="example"></a>Przykład  
 Usługa, która jest używana z kodu klienta, który jest używany w poprzedniej procedurze implementuje `ICalculator` interfejsu, jak pokazano w poniższym kodzie. Na stronie usługi `Add` i `Subtract` operacji kontraktu jest wywołana synchronicznie przez Windows Communication Foundation (WCF) w czasie wykonywania, nawet jeśli poprzednie kroki klienta są wywoływane asynchronicznie na komputerze klienckim. `Multiply` i `Divide` operacje są używane do wywoływania usługi asynchronicznie po stronie usługi, nawet wtedy, gdy klient wywołuje je synchronicznie. W tym przykładzie <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwość `true`. Ustawienie właściwości w połączeniu z implementacją [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wzorca asynchronicznego, informuje o czasie wykonywania wywołania operacji asynchronicznie.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontraktu usługi: Przykład asynchronicznego](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
