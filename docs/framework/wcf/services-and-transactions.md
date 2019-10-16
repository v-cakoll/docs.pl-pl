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
# <a name="services-and-transactions"></a><span data-ttu-id="2d7bf-102">Usługi i transakcje</span><span class="sxs-lookup"><span data-stu-id="2d7bf-102">Services and Transactions</span></span>
<span data-ttu-id="2d7bf-103">Aplikacje Windows Communication Foundation (WCF) mogą inicjować transakcję z poziomu klienta i koordynować transakcję w ramach operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="2d7bf-104">Klienci mogą inicjować transakcję i wywoływać kilka operacji usługi i zapewnić, że operacje usługi są zatwierdzane lub wycofywane jako pojedyncza jednostka.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="2d7bf-105">Zachowanie transakcji można włączyć w kontrakcie usługi, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawiając jego właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> dla operacji usługi, które wymagają transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="2d7bf-106">Parametr <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Określa, czy transakcja, w której wykonywana jest metoda, jest automatycznie uzupełniana w przypadku nieobsłużonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="2d7bf-107">Aby uzyskać więcej informacji na temat tych atrybutów, zobacz [atrybuty transakcji ServiceModel](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2d7bf-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="2d7bf-108">Prace wykonywane w ramach operacji usługi i zarządzane przez Menedżera zasobów, takie jak rejestrowanie aktualizacji bazy danych, są częścią transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="2d7bf-109">Poniższy przykład ilustruje użycie atrybutów <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> w celu kontrolowania zachowania transakcji po stronie usług.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="2d7bf-110">Można włączyć transakcje i przepływ transakcji, konfigurując powiązania klienta i usługi w celu użycia protokołu WS-AtomicTransaction i ustawiając element [\<transactionFlow >](../configure-apps/file-schema/wcf/transactionflow.md) na `true`, jak pokazano w poniższym przykładzie. skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="2d7bf-111">Klienci mogą rozpocząć transakcję, tworząc <xref:System.Transactions.TransactionScope> i wywołując operacje usługi w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="2d7bf-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d7bf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d7bf-112">See also</span></span>

- [<span data-ttu-id="2d7bf-113">Obsługa transakcyjna w elemencie System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2d7bf-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="2d7bf-114">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="2d7bf-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="2d7bf-115">Przepływ transakcji WS</span><span class="sxs-lookup"><span data-stu-id="2d7bf-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
