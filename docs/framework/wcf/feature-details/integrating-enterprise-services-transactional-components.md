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
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw

Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami przedsiębiorstwa (zobacz [Integrowanie z aplikacjami com+](integrating-with-com-plus-applications.md)). Można jednak zapewnić elastyczność w programowaniu usług, które wewnętrznie korzystają ze składników transakcyjnych hostowanych w ramach usług przedsiębiorstwa. Ze względu na to, że funkcja transakcji WCF jest oparta na <xref:System.Transactions> infrastrukturze, proces integrowania usług przedsiębiorstwa z programem WCF jest taki sam jak w przypadku określania współdziałania między <xref:System.Transactions> usługami i usług przedsiębiorstwa, jak opisano w obszarze [współdziałanie z usługami przedsiębiorstwa i transakcjami modelu COM+](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Aby zapewnić żądany poziom współdziałania między przychodzącą transakcję i transakcją kontekstu modelu COM+, implementacja usługi musi utworzyć <xref:System.Transactions.TransactionScope> wystąpienie i użyć odpowiedniej wartości z <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrowanie usług przedsiębiorstwa z operacją usługi  
 Poniższy kod ilustruje operację z dozwolonym przepływem transakcji, która tworzy <xref:System.Transactions.TransactionScope> za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opcji. W tym scenariuszu mają zastosowanie następujące warunki:  
  
- Jeśli klient przeprowadzi transakcję, operacja, łącznie z wywołaniem składnika usług przedsiębiorstwa, jest wykonywana w zakresie tej transakcji. Użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest synchronizowana z <xref:System.EnterpriseServices> kontekstem, co oznacza, że otoczenia transakcja dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.  
  
- Jeśli klient nie tworzy przepływu transakcji, ustawienie powoduje <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` utworzenie nowego zakresu transakcji dla operacji. Podobnie użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja operacji jest taka sama jak transakcja używana wewnątrz <xref:System.EnterpriseServices> kontekstu składnika.  
  
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
  
 Jeśli nie jest wymagana żadna synchronizacja między bieżącą transakcją operacji i wywołaniami składników transakcyjnych usług przedsiębiorstwa, użyj <xref:System.Transactions.EnterpriseServicesInteropOption.None> opcji podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrowanie usług przedsiębiorstwa z klientem  
 Poniższy kod ilustruje kod klienta przy użyciu <xref:System.Transactions.TransactionScope> wystąpienia z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ustawieniem. W tym scenariuszu wywołania operacji usługi obsługujące przepływ transakcji są wykonywane w ramach tej samej transakcji co wywołania składników usług przedsiębiorstwa.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Integrowanie z aplikacjami COM+](integrating-with-com-plus-applications.md)
- [Współdziałanie z aplikacjami COM](integrating-with-com-applications.md)
