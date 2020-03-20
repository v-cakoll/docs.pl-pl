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
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw

Windows Communication Foundation (WCF) zapewnia automatyczny mechanizm integracji z usługami dla przedsiębiorstw (patrz [Integracja z aplikacjami COM+).](integrating-with-com-plus-applications.md) Jednak można chcieć elastyczności do tworzenia usług, które wewnętrznie używają składników transakcyjnych hostowanych w ramach usług Enterprise Services. Ponieważ funkcja Transakcje WCF jest <xref:System.Transactions> zbudowana na infrastrukturze, proces integracji usług dla przedsiębiorstw z WCF jest identyczny z procesem określania interoperacyjności między usługami <xref:System.Transactions> dla przedsiębiorstw i usługami dla przedsiębiorstw, zgodnie z opisem w obszarze [Interoperacyjność z usługami dla przedsiębiorstw i transakcjami COM+.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))  
  
 Aby zapewnić żądany poziom współdziałania między przychodzącą przebytą transakcją a <xref:System.Transactions.TransactionScope> transakcją kontekstu COM+, implementacja usługi musi utworzyć wystąpienie i użyć odpowiedniej wartości z wyliczenia. <xref:System.Transactions.EnterpriseServicesInteropOption>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integracja usług dla przedsiębiorstw z operacją serwisową  
 Poniższy kod demonstruje operację z dozwolonym przepływem <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> transakcji, która tworzy z opcją. W tym scenariuszu obowiązują następujące warunki:  
  
- Jeśli klient przepływa transakcję, operacja, w tym wywołanie składnika Usługi dla przedsiębiorstw, jest wykonywana w zakresie tej transakcji. Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że transakcja jest <xref:System.EnterpriseServices> synchronizowana z kontekstem, <xref:System.Transactions> co <xref:System.EnterpriseServices> oznacza, że transakcja otoczenia dla i jest taka sama.  
  
- Jeśli klient nie przepływa transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` tworzy nowy zakres transakcji dla operacji. Podobnie przy <xref:System.Transactions.EnterpriseServicesInteropOption.Full> użyciu zapewnia, że operacja transakcji jest taka sama <xref:System.EnterpriseServices> jak transakcja używana w kontekście składnika.  
  
 Wszelkie wywołania dodatkowe metody również występują w zakresie transakcji tej samej operacji.  
  
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
  
 Jeśli synchronizacja nie jest wymagana między bieżącą transakcją operacji a wywołaniem <xref:System.Transactions.EnterpriseServicesInteropOption.None> transakcyjnych składników <xref:System.Transactions.TransactionScope> usług Enterprise Services, użyj tej opcji podczas tworzenia wystąpienia wystąpienia wystąpienia.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integracja usług dla przedsiębiorstw z klientem  
 Poniższy kod demonstruje <xref:System.Transactions.TransactionScope> kod klienta <xref:System.Transactions.EnterpriseServicesInteropOption.Full> przy użyciu wystąpienia z ustawieniem. W tym scenariuszu wywołania operacji usługi, które obsługują przepływ transakcji występują w zakresie tej samej transakcji, jak wywołania składników usług Dla przedsiębiorstwa.  
  
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

- [Integracja z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Współdziałanie z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
