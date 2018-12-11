---
title: Usługi i transakcje
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 2e37a42b3767d279da0d742ba9958ceb6628aab1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236976"
---
# <a name="services-and-transactions"></a><span data-ttu-id="0ae65-102">Usługi i transakcje</span><span class="sxs-lookup"><span data-stu-id="0ae65-102">Services and Transactions</span></span>
<span data-ttu-id="0ae65-103">Aplikacje Windows Communication Foundation (WCF) zainicjować transakcji z w ramach klienta oraz koordynowanie transakcji w ramach operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="0ae65-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="0ae65-104">Klienci mogą inicjować transakcji i wywoływanie kilka operacji usług i upewnij się, że operacje usług są albo przekazana lub wycofana jako pojedyncza jednostka.</span><span class="sxs-lookup"><span data-stu-id="0ae65-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="0ae65-105">Zachowanie transakcji w kontrakcie usługi można włączyć, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawienie jej <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwości operacje usługi, które wymagają klienta transakcji.</span><span class="sxs-lookup"><span data-stu-id="0ae65-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="0ae65-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr określa, czy transakcji, w którym metoda jest wykonywana jest wprowadzana automatycznie, jeśli nie nieobsłużone wyjątki są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="0ae65-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="0ae65-107">Aby uzyskać więcej informacji o tych atrybutów, zobacz [atrybuty transakcji elementu ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0ae65-107">For more information about these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="0ae65-108">Praca odbywa się w zakresie operacji usług i zarządzane przez Menedżera zasobów, takich jak rejestrowanie aktualizacji bazy danych jest częścią transakcji firmy klienta.</span><span class="sxs-lookup"><span data-stu-id="0ae65-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="0ae65-109">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty kontrolować zachowanie transakcji po stronie usługi.</span><span class="sxs-lookup"><span data-stu-id="0ae65-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
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
  
 <span data-ttu-id="0ae65-110">Możesz włączyć transakcji i transakcja powiązania do używania protokołu WS-AtomicTransaction oraz ustawienia usługi i przepływać przez konfigurowanie klienta [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elementu `true`, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="0ae65-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="0ae65-111">Klientów można rozpocząć transakcji, tworząc <xref:System.Transactions.TransactionScope> i wywoływanie operacji usługi w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="0ae65-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ae65-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ae65-112">See Also</span></span>  
 [<span data-ttu-id="0ae65-113">Obsługa transakcyjna w elemencie System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0ae65-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [<span data-ttu-id="0ae65-114">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="0ae65-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [<span data-ttu-id="0ae65-115">Przepływ transakcji WS</span><span class="sxs-lookup"><span data-stu-id="0ae65-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
