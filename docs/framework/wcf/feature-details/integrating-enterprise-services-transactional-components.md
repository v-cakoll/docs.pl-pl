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
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw

Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami przedsiębiorstwa (zobacz [Integrowanie z aplikacjami com+](integrating-with-com-plus-applications.md)). Można jednak zapewnić elastyczność w programowaniu usług, które wewnętrznie korzystają ze składników transakcyjnych hostowanych w ramach usług przedsiębiorstwa. Ponieważ funkcja transakcji WCF jest oparta na infrastrukturze <xref:System.Transactions>, proces integrowania usług przedsiębiorstwa z WCF jest taki sam jak w przypadku określania współdziałania między usługami <xref:System.Transactions> i Enterprise, jak opisano w temacie [współdziałanie z usługami przedsiębiorstwa i transakcjami modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Aby zapewnić żądany poziom współdziałania między przychodzącą transakcję i transakcją kontekstu modelu COM+, implementacja usługi musi utworzyć wystąpienie <xref:System.Transactions.TransactionScope> i użyć odpowiedniej wartości z wyliczenia <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrowanie usług przedsiębiorstwa z operacją usługi  
 Poniższy kod ilustruje operację z dozwolonym przepływem transakcji, która tworzy <xref:System.Transactions.TransactionScope> z opcją <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. W tym scenariuszu mają zastosowanie następujące warunki:  
  
- Jeśli klient przeprowadzi transakcję, operacja, łącznie z wywołaniem składnika usług przedsiębiorstwa, jest wykonywana w zakresie tej transakcji. Przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja jest synchronizowana z kontekstem <xref:System.EnterpriseServices>, co oznacza, że otoczenia transakcji dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.  
  
- Jeśli klient nie przepływ transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> na `true` tworzy nowy zakres transakcji dla operacji. Podobnie przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja operacji jest taka sama jak transakcja używana wewnątrz kontekstu składnika <xref:System.EnterpriseServices>.  
  
 Wszelkie dodatkowe wywołania metod są również wykonywane w ramach transakcji w ramach tej samej operacji.  
  
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
  
 Jeśli nie jest wymagana żadna synchronizacja między bieżącą transakcją operacji i wywołaniami składników transakcyjnych usług przedsiębiorstwa, użyj opcji <xref:System.Transactions.EnterpriseServicesInteropOption.None> podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrowanie usług przedsiębiorstwa z klientem  
 Poniższy kod ilustruje kod klienta przy użyciu <xref:System.Transactions.TransactionScope> wystąpienia z ustawieniem <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. W tym scenariuszu wywołania operacji usługi obsługujące przepływ transakcji są wykonywane w ramach tej samej transakcji co wywołania składników usług przedsiębiorstwa.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Współdziałanie z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
