---
title: Usługi i transakcje
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143281"
---
# <a name="services-and-transactions"></a>Usługi i transakcje
Aplikacje Windows Communication Foundation (WCF) mogą inicjować transakcję z poziomu klienta i koordynować transakcję w ramach operacji usługi. Klienci mogą inicjować transakcję i wywoływać kilka operacji usługi i upewnić się, że operacje usługi są zatwierdzone lub wycofane jako pojedyncza jednostka.  
  
 Zachowanie transakcji można włączyć w umowie serwisowej, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawiając jego <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwości dla operacji usługi, które wymagają transakcji klienta. Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> określa, czy transakcja, w której wykonuje metodę jest automatycznie wykonywane, jeśli nie są zgłaszane nieobsługiwane wyjątki. Aby uzyskać więcej informacji na temat tych atrybutów, zobacz [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).  
  
 Praca wykonywana w operacjach usługi i zarządzana przez menedżera zasobów, na przykład rejestrowanie aktualizacji bazy danych, jest częścią transakcji klienta.  
  
 Poniższy przykład pokazuje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> i atrybuty do kontrolowania zachowania transakcji po stronie usługi.  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 Można włączyć transakcje i przepływ transakcji, konfigurując powiązania klienta i usługi do używania protokołu WS-AtomicTransaction `true`i ustawiając [ \<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element , jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 Klienci mogą rozpocząć transakcję, <xref:System.Transactions.TransactionScope> tworząc i wywołując operacje usługi w zakresie transakcji.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa transakcyjna w elemencie System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modele transakcji](./feature-details/transaction-models.md)
- [Przepływ transakcji WS](./samples/ws-transaction-flow.md)
