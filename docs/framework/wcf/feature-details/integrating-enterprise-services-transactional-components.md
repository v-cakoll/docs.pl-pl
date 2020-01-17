---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 5914f76639adc3ff569a3bfb8d6eb1db14313e76
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211940"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="a2ede-102">Integrowanie składników transakcyjnych usług dla przedsiębiorstw</span><span class="sxs-lookup"><span data-stu-id="a2ede-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="a2ede-103">Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami przedsiębiorstwa (zobacz [Integrowanie z aplikacjami com+](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="a2ede-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="a2ede-104">Można jednak zapewnić elastyczność w programowaniu usług, które wewnętrznie korzystają ze składników transakcyjnych hostowanych w ramach usług przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="a2ede-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="a2ede-105">Ponieważ funkcja transakcji WCF jest oparta na infrastrukturze <xref:System.Transactions>, proces integrowania usług przedsiębiorstwa z WCF jest taki sam jak w przypadku określania współdziałania między usługami <xref:System.Transactions> i Enterprise, jak opisano w temacie [współdziałanie z usługami przedsiębiorstwa i transakcjami modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="a2ede-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="a2ede-106">Aby zapewnić żądany poziom współdziałania między przychodzącą transakcję i transakcją kontekstu modelu COM+, implementacja usługi musi utworzyć wystąpienie <xref:System.Transactions.TransactionScope> i użyć odpowiedniej wartości z wyliczenia <xref:System.Transactions.EnterpriseServicesInteropOption>.</span><span class="sxs-lookup"><span data-stu-id="a2ede-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="a2ede-107">Integrowanie usług przedsiębiorstwa z operacją usługi</span><span class="sxs-lookup"><span data-stu-id="a2ede-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="a2ede-108">Poniższy kod ilustruje operację z dozwolonym przepływem transakcji, która tworzy <xref:System.Transactions.TransactionScope> z opcją <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.</span><span class="sxs-lookup"><span data-stu-id="a2ede-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="a2ede-109">W tym scenariuszu mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="a2ede-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="a2ede-110">Jeśli klient przeprowadzi transakcję, operacja, łącznie z wywołaniem składnika usług przedsiębiorstwa, jest wykonywana w zakresie tej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a2ede-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="a2ede-111">Przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja jest synchronizowana z kontekstem <xref:System.EnterpriseServices>, co oznacza, że otoczenia transakcji dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="a2ede-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="a2ede-112">Jeśli klient nie przepływ transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> na `true` tworzy nowy zakres transakcji dla operacji.</span><span class="sxs-lookup"><span data-stu-id="a2ede-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="a2ede-113">Podobnie przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja operacji jest taka sama jak transakcja używana wewnątrz kontekstu składnika <xref:System.EnterpriseServices>.</span><span class="sxs-lookup"><span data-stu-id="a2ede-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="a2ede-114">Wszelkie dodatkowe wywołania metod są również wykonywane w ramach transakcji w ramach tej samej operacji.</span><span class="sxs-lookup"><span data-stu-id="a2ede-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="a2ede-115">Jeśli nie jest wymagana żadna synchronizacja między bieżącą transakcją operacji i wywołaniami składników transakcyjnych usług przedsiębiorstwa, użyj opcji <xref:System.Transactions.EnterpriseServicesInteropOption.None> podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a2ede-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="a2ede-116">Integrowanie usług przedsiębiorstwa z klientem</span><span class="sxs-lookup"><span data-stu-id="a2ede-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="a2ede-117">Poniższy kod ilustruje kod klienta przy użyciu <xref:System.Transactions.TransactionScope> wystąpienia z ustawieniem <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.</span><span class="sxs-lookup"><span data-stu-id="a2ede-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="a2ede-118">W tym scenariuszu wywołania operacji usługi obsługujące przepływ transakcji są wykonywane w ramach tej samej transakcji co wywołania składników usług przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="a2ede-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2ede-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2ede-119">See also</span></span>

- [<span data-ttu-id="a2ede-120">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="a2ede-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a2ede-121">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="a2ede-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
