---
title: "Usługi i transakcje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6256db06825a79b5235b92e2ed205608f04aac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="services-and-transactions"></a><span data-ttu-id="b5e47-102">Usługi i transakcje</span><span class="sxs-lookup"><span data-stu-id="b5e47-102">Services and Transactions</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="b5e47-103">aplikacje można zainicjować transakcji od klienta programu i koordynacji transakcji w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="b5e47-103"> applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="b5e47-104">Klienci mogą zainicjować transakcji i wywołać kilka operacji usługi i upewnij się, że operacje usługi są zatwierdzona lub wycofana jako pojedyncza jednostka.</span><span class="sxs-lookup"><span data-stu-id="b5e47-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="b5e47-105">Zachowanie transakcji w kontrakcie usługi można włączyć, określając <xref:System.ServiceModel.ServiceBehaviorAttribute> i ustawienie jej <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwości dla operacji usługi, które wymagają klienta transakcji.</span><span class="sxs-lookup"><span data-stu-id="b5e47-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="b5e47-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Parametr określa, czy transakcja, w której wykonuje metodę jest wprowadzana automatycznie, jeśli nie nieobsługiwane wyjątki są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="b5e47-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b5e47-107">te atrybuty, zobacz [atrybuty transakcji elementu ServiceModel](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5e47-107"> these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="b5e47-108">Praca jest wykonywana w ramach operacji usługi i zarządzany przez Menedżera zasobów, takich jak rejestrowanie aktualizacje bazy danych jest częścią transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="b5e47-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="b5e47-109">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty do kontrolowania zachowania transakcji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="b5e47-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="b5e47-110">Można włączyć transakcji i transakcji przepływać przez skonfigurowanie klienta i usługi powiązania do korzystania z protokołu WS-AtomicTransaction oraz ustawienie [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) elementu `true`, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b5e47-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b5e47-111">Klientów można rozpocząć transakcji, tworząc <xref:System.Transactions.TransactionScope> i wywoływanie operacji usługi w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="b5e47-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5e47-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5e47-112">See Also</span></span>  
 [<span data-ttu-id="b5e47-113">Obsługa transakcyjna w elemencie System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b5e47-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [<span data-ttu-id="b5e47-114">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="b5e47-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [<span data-ttu-id="b5e47-115">Przepływ transakcji WS</span><span class="sxs-lookup"><span data-stu-id="b5e47-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
