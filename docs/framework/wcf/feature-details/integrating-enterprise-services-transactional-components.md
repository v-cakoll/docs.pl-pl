---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 8453b4199f5e6eae263ebc3fc1c457429c868d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492515"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="55ccd-102">Integrowanie składników transakcyjnych usług dla przedsiębiorstw</span><span class="sxs-lookup"><span data-stu-id="55ccd-102">Integrating Enterprise Services Transactional Components</span></span>
<span data-ttu-id="55ccd-103">Windows Communication Foundation (WCF) zapewnia mechanizm automatycznego do integracji z usługami przedsiębiorstwa (zobacz [współdziałanie z aplikacjami COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="55ccd-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="55ccd-104">Może być jednak elastyczność tworzenia usług używających wewnętrznie składników transakcyjnych hostowanych w ramach usług dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="55ccd-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="55ccd-105">Ponieważ funkcja transakcji WCF jest oparty na <xref:System.Transactions> infrastruktury, proces integracji usług dla przedsiębiorstw z WCF jest identyczna jak służący do określania współdziałanie <xref:System.Transactions> i usług dla przedsiębiorstw, w sposób opisany w [Współdziałanie z usługami przedsiębiorstwa i transakcje COM +](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="55ccd-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="55ccd-106">Aby zapewnić żądany poziom współdziałanie transakcji przychodzącej i transakcji kontekstu modelu COM +, należy utworzyć implementacji usługi <xref:System.Transactions.TransactionScope> wystąpienia i użyj odpowiednią wartość z <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="55ccd-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="55ccd-107">Integrowanie usług dla przedsiębiorstw z operacji usługi</span><span class="sxs-lookup"><span data-stu-id="55ccd-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="55ccd-108">Poniższy kod przedstawia operacji z użyciem przepływu transakcji dozwolone, która tworzy <xref:System.Transactions.TransactionScope> z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opcji.</span><span class="sxs-lookup"><span data-stu-id="55ccd-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="55ccd-109">W tym scenariuszu mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="55ccd-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="55ccd-110">Jeśli klient przepływu transakcji, wykonaniem operacji, w tym wywołaniu składnika usług dla przedsiębiorstw w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="55ccd-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="55ccd-111">Przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest zsynchronizowany z <xref:System.EnterpriseServices> kontekstu, co oznacza, że transakcja otoczenia dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="55ccd-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="55ccd-112">Jeśli klient nie przepływu transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> do `true` tworzy nowy zakres transakcji dla tej operacji.</span><span class="sxs-lookup"><span data-stu-id="55ccd-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="55ccd-113">Podobnie za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że operacji transakcji jest taki sam, jak używać wewnątrz transakcji <xref:System.EnterpriseServices> kontekście składnika.</span><span class="sxs-lookup"><span data-stu-id="55ccd-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="55ccd-114">Wszystkie wywołania metody dodatkowe także wystąpić w zakresie transakcji tej samej operacji.</span><span class="sxs-lookup"><span data-stu-id="55ccd-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```  
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
  
 <span data-ttu-id="55ccd-115">Jeśli synchronizacja nie jest wymagany między operacji bieżącej transakcji i wywołania składników transakcyjnych usług dla przedsiębiorstw, należy użyć <xref:System.Transactions.EnterpriseServicesInteropOption.None> podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="55ccd-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="55ccd-116">Integrowanie usług dla przedsiębiorstw, za pomocą klienta</span><span class="sxs-lookup"><span data-stu-id="55ccd-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="55ccd-117">Poniższy kod przedstawia kodu klienta za pomocą <xref:System.Transactions.TransactionScope> wystąpienia z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ustawienie.</span><span class="sxs-lookup"><span data-stu-id="55ccd-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="55ccd-118">W tym scenariuszu wywołania do operacji usługi, które obsługują przepływu transakcji występuje w zakresie jednej transakcji wywołania metody składniki usług dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="55ccd-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="55ccd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55ccd-119">See Also</span></span>  
 [<span data-ttu-id="55ccd-120">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="55ccd-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="55ccd-121">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="55ccd-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
