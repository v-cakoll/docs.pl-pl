---
title: Usługi i transakcje
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9110198fa64e43c20e1e6ba0dcf158dddeac93a6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321152"
---
# <a name="services-and-transactions"></a>Usługi i transakcje
Aplikacje Windows Communication Foundation (WCF) mogą inicjować transakcję z poziomu klienta i koordynować transakcję w ramach operacji usługi. Klienci mogą inicjować transakcję i wywoływać kilka operacji usługi i zapewnić, że operacje usługi są zatwierdzane lub wycofywane jako pojedyncza jednostka.  
  
 Zachowanie transakcji można włączyć w kontrakcie usługi, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawiając jego właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> dla operacji usługi, które wymagają transakcji klienta. Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Określa, czy transakcja, w której wykonywana jest metoda, jest automatycznie uzupełniana w przypadku nieobsłużonych wyjątków. Aby uzyskać więcej informacji na temat tych atrybutów, zobacz [atrybuty transakcji ServiceModel](./feature-details/servicemodel-transaction-attributes.md).  
  
 Prace wykonywane w ramach operacji usługi i zarządzane przez Menedżera zasobów, takie jak rejestrowanie aktualizacji bazy danych, są częścią transakcji klienta.  
  
 Poniższy przykład ilustruje użycie atrybutów <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> w celu kontrolowania zachowania transakcji po stronie usług.  
  
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
  
 Można włączyć transakcje i przepływ transakcji, konfigurując powiązania klienta i usługi w celu użycia protokołu WS-AtomicTransaction i ustawiając element [\<transactionFlow >](../configure-apps/file-schema/wcf/transactionflow.md) na `true`, jak pokazano w poniższym przykładzie. skonfigurować.  
  
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
  
 Klienci mogą rozpocząć transakcję, tworząc <xref:System.Transactions.TransactionScope> i wywołując operacje usługi w zakresie transakcji.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa transakcyjna w elemencie System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modele transakcji](./feature-details/transaction-models.md)
- [Przepływ transakcji WS](./samples/ws-transaction-flow.md)
