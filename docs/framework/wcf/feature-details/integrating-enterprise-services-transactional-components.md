---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1c4fabfadb113c79b216fa10ff80b551ba0f9716
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596854"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="1ec4d-102">Integrowanie składników transakcyjnych usług dla przedsiębiorstw</span><span class="sxs-lookup"><span data-stu-id="1ec4d-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="1ec4d-103">Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami przedsiębiorstwa (zobacz [Integrowanie z aplikacjami com+](integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="1ec4d-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="1ec4d-104">Można jednak zapewnić elastyczność w programowaniu usług, które wewnętrznie korzystają ze składników transakcyjnych hostowanych w ramach usług przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="1ec4d-105">Ze względu na to, że funkcja transakcji WCF jest oparta na <xref:System.Transactions> infrastrukturze, proces integrowania usług przedsiębiorstwa z programem WCF jest taki sam jak w przypadku określania współdziałania między <xref:System.Transactions> usługami i usług przedsiębiorstwa, jak opisano w obszarze [współdziałanie z usługami przedsiębiorstwa i transakcjami modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1ec4d-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="1ec4d-106">Aby zapewnić żądany poziom współdziałania między przychodzącą transakcję i transakcją kontekstu modelu COM+, implementacja usługi musi utworzyć <xref:System.Transactions.TransactionScope> wystąpienie i użyć odpowiedniej wartości z <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="1ec4d-107">Integrowanie usług przedsiębiorstwa z operacją usługi</span><span class="sxs-lookup"><span data-stu-id="1ec4d-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="1ec4d-108">Poniższy kod ilustruje operację z dozwolonym przepływem transakcji, która tworzy <xref:System.Transactions.TransactionScope> za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opcji.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="1ec4d-109">W tym scenariuszu mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="1ec4d-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="1ec4d-110">Jeśli klient przeprowadzi transakcję, operacja, łącznie z wywołaniem składnika usług przedsiębiorstwa, jest wykonywana w zakresie tej transakcji.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="1ec4d-111">Użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest synchronizowana z <xref:System.EnterpriseServices> kontekstem, co oznacza, że otoczenia transakcja dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="1ec4d-112">Jeśli klient nie tworzy przepływu transakcji, ustawienie powoduje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` utworzenie nowego zakresu transakcji dla operacji.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="1ec4d-113">Podobnie użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja operacji jest taka sama jak transakcja używana wewnątrz <xref:System.EnterpriseServices> kontekstu składnika.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="1ec4d-114">Wszelkie dodatkowe wywołania metod są również wykonywane w ramach transakcji w ramach tej samej operacji.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="1ec4d-115">Jeśli nie jest wymagana żadna synchronizacja między bieżącą transakcją operacji i wywołaniami składników transakcyjnych usług przedsiębiorstwa, użyj <xref:System.Transactions.EnterpriseServicesInteropOption.None> opcji podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="1ec4d-116">Integrowanie usług przedsiębiorstwa z klientem</span><span class="sxs-lookup"><span data-stu-id="1ec4d-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="1ec4d-117">Poniższy kod ilustruje kod klienta przy użyciu <xref:System.Transactions.TransactionScope> wystąpienia z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="1ec4d-118">W tym scenariuszu wywołania operacji usługi obsługujące przepływ transakcji są wykonywane w ramach tej samej transakcji co wywołania składników usług przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ec4d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ec4d-119">See also</span></span>

- [<span data-ttu-id="1ec4d-120">Integrowanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="1ec4d-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="1ec4d-121">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="1ec4d-121">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
