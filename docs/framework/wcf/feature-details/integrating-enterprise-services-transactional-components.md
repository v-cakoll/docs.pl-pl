---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: c73be31bef67f1de818f7b04181a3540bbd7caa8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991548"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw
Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami przedsiębiorstwa (zobacz [Integrowanie z aplikacjami com+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Można jednak zapewnić elastyczność w programowaniu usług, które wewnętrznie korzystają ze składników transakcyjnych hostowanych w ramach usług przedsiębiorstwa. Ze względu na to, że funkcja transakcji <xref:System.Transactions> WCF jest oparta na infrastrukturze, proces integrowania usług przedsiębiorstwa z programem WCF jest taki sam <xref:System.Transactions> jak w przypadku określania współdziałania między i usług przedsiębiorstwa, zgodnie z opisem w temacie [Współdziałanie z usługami przedsiębiorstwa i transakcjami modelu COM+](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Aby zapewnić żądany poziom współdziałania między przychodzącą transakcję i transakcją kontekstu modelu COM+, implementacja usługi musi utworzyć <xref:System.Transactions.TransactionScope> wystąpienie i użyć odpowiedniej wartości <xref:System.Transactions.EnterpriseServicesInteropOption> z wyliczenia.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrowanie usług przedsiębiorstwa z operacją usługi  
 Poniższy kod ilustruje operację z dozwolonym przepływem transakcji, która tworzy <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> za pomocą opcji. W tym scenariuszu mają zastosowanie następujące warunki:  
  
- Jeśli klient przeprowadzi transakcję, operacja, łącznie z wywołaniem składnika usług przedsiębiorstwa, jest wykonywana w zakresie tej transakcji. Użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest synchronizowana <xref:System.EnterpriseServices> z kontekstem, co oznacza, że <xref:System.EnterpriseServices> otoczenia transakcja dla <xref:System.Transactions> i jest taka sama.  
  
- Jeśli klient nie tworzy przepływu transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` powoduje utworzenie nowego zakresu transakcji dla operacji. Podobnie użycie <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja operacji jest taka sama jak transakcja używana <xref:System.EnterpriseServices> wewnątrz kontekstu składnika.  
  
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
 Poniższy kod ilustruje kod klienta przy użyciu <xref:System.Transactions.TransactionScope> wystąpienia <xref:System.Transactions.EnterpriseServicesInteropOption.Full> z ustawieniem. W tym scenariuszu wywołania operacji usługi obsługujące przepływ transakcji są wykonywane w ramach tej samej transakcji co wywołania składników usług przedsiębiorstwa.  
  
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
