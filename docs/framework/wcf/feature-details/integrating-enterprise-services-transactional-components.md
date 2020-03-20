---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184736"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="18f68-102">Integrowanie składników transakcyjnych usług dla przedsiębiorstw</span><span class="sxs-lookup"><span data-stu-id="18f68-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="18f68-103">Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami dla przedsiębiorstw (patrz [Integracja z aplikacjami COM+).](integrating-with-com-plus-applications.md)</span><span class="sxs-lookup"><span data-stu-id="18f68-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="18f68-104">Jednak można chcieć elastyczności do tworzenia usług, które wewnętrznie używają składników transakcyjnych hostowanych w ramach usług Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="18f68-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="18f68-105">Ponieważ funkcja Transakcje WCF jest <xref:System.Transactions> zbudowana na infrastrukturze, proces integracji usług dla przedsiębiorstw z WCF jest identyczny z procesem określania interoperacyjności między usługami <xref:System.Transactions> dla przedsiębiorstw i usługami dla przedsiębiorstw, zgodnie z opisem w obszarze [Interoperacyjność z usługami dla przedsiębiorstw i transakcjami COM+.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="18f68-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="18f68-106">Aby zapewnić żądany poziom współdziałania między przychodzącą przebytą transakcją a <xref:System.Transactions.TransactionScope> transakcją kontekstu COM+, implementacja usługi musi utworzyć wystąpienie i użyć odpowiedniej wartości z wyliczenia. <xref:System.Transactions.EnterpriseServicesInteropOption></span><span class="sxs-lookup"><span data-stu-id="18f68-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="18f68-107">Integracja usług dla przedsiębiorstw z operacją serwisową</span><span class="sxs-lookup"><span data-stu-id="18f68-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="18f68-108">Poniższy kod demonstruje operację z dozwolonym przepływem <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> transakcji, która tworzy z opcją.</span><span class="sxs-lookup"><span data-stu-id="18f68-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="18f68-109">W tym scenariuszu obowiązują następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="18f68-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="18f68-110">Jeśli klient przepływa transakcję, operacja, w tym wywołanie składnika Usługi dla przedsiębiorstw, jest wykonywana w zakresie tej transakcji.</span><span class="sxs-lookup"><span data-stu-id="18f68-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="18f68-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja jest <xref:System.EnterpriseServices> synchronizowana z kontekstem, <xref:System.Transactions> co <xref:System.EnterpriseServices> oznacza, że transakcja otoczenia dla i jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="18f68-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="18f68-112">Jeśli klient nie przepływa transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` tworzy nowy zakres transakcji dla operacji.</span><span class="sxs-lookup"><span data-stu-id="18f68-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="18f68-113">Podobnie przy <xref:System.Transactions.EnterpriseServicesInteropOption.Full> użyciu zapewnia, że operacja transakcji jest taka sama <xref:System.EnterpriseServices> jak transakcja używana w kontekście składnika.</span><span class="sxs-lookup"><span data-stu-id="18f68-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="18f68-114">Wszelkie wywołania dodatkowe metody również występują w zakresie transakcji tej samej operacji.</span><span class="sxs-lookup"><span data-stu-id="18f68-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
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
  
 <span data-ttu-id="18f68-115">Jeśli synchronizacja nie jest wymagana między bieżącą transakcją operacji a wywołaniem <xref:System.Transactions.EnterpriseServicesInteropOption.None> transakcyjnych składników <xref:System.Transactions.TransactionScope> usług Enterprise Services, użyj tej opcji podczas tworzenia wystąpienia wystąpienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="18f68-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="18f68-116">Integracja usług dla przedsiębiorstw z klientem</span><span class="sxs-lookup"><span data-stu-id="18f68-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="18f68-117">Poniższy kod demonstruje <xref:System.Transactions.TransactionScope> kod klienta <xref:System.Transactions.EnterpriseServicesInteropOption.Full> przy użyciu wystąpienia z ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="18f68-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="18f68-118">W tym scenariuszu wywołania operacji usługi, które obsługują przepływ transakcji występują w zakresie tej samej transakcji, jak wywołania składników usług Dla przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="18f68-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18f68-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18f68-119">See also</span></span>

- [<span data-ttu-id="18f68-120">Integracja z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="18f68-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="18f68-121">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="18f68-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
