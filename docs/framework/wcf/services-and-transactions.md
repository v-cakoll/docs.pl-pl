---
title: Usługi i transakcje
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 9dfe34406bfda2c16bd2f0cd53796b2fcef07b57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138336"
---
# <a name="services-and-transactions"></a>Usługi i transakcje
Aplikacje Windows Communication Foundation (WCF) zainicjować transakcji z w ramach klienta oraz koordynowanie transakcji w ramach operacji usługi. Klienci mogą inicjować transakcji i wywoływanie kilka operacji usług i upewnij się, że operacje usług są albo przekazana lub wycofana jako pojedyncza jednostka.  
  
 Zachowanie transakcji w kontrakcie usługi można włączyć, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawienie jej <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwości operacje usługi, które wymagają klienta transakcji. <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr określa, czy transakcji, w którym metoda jest wykonywana jest wprowadzana automatycznie, jeśli nie nieobsłużone wyjątki są zgłaszane. Aby uzyskać więcej informacji o tych atrybutów, zobacz [atrybuty transakcji elementu ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
 Praca odbywa się w zakresie operacji usług i zarządzane przez Menedżera zasobów, takich jak rejestrowanie aktualizacji bazy danych jest częścią transakcji firmy klienta.  
  
 W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty kontrolować zachowanie transakcji po stronie usługi.  
  
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
  
 Możesz włączyć transakcji i transakcja powiązania do używania protokołu WS-AtomicTransaction oraz ustawienia usługi i przepływać przez konfigurowanie klienta [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elementu `true`, jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
 Klientów można rozpocząć transakcji, tworząc <xref:System.Transactions.TransactionScope> i wywoływanie operacji usługi w zakresie transakcji.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa transakcyjna w elemencie System.ServiceModel](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)
- [Modele transakcji](../../../docs/framework/wcf/feature-details/transaction-models.md)
- [Przepływ transakcji WS](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
