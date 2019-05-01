---
title: Integrowanie składników transakcyjnych usług dla przedsiębiorstw
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 33e09eab1d7ad24dc234cfff21e352611e0b2ef9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047038"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw
Windows Communication Foundation (WCF) zapewnia mechanizm automatycznego w celu integracji z usługami przedsiębiorstwa (zobacz [współdziałanie z aplikacjami COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Jednak możesz elastyczność do tworzenia usług korzystających z wewnętrznie składników transakcyjnych obsługiwany w ramach usług dla przedsiębiorstw. Ponieważ funkcja transakcji WCF jest oparta na <xref:System.Transactions> infrastruktury, proces integracji usług dla przedsiębiorstw z usługą WCF jest identyczna jak do określania współdziałanie <xref:System.Transactions> i usług dla przedsiębiorstw, co zostało opisane w [Współdziałanie z usługami przedsiębiorstwa i transakcjami COM +](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Aby zapewnić żądany poziom współdziałania między przychodzących transakcji i transakcji COM + kontekstu, należy utworzyć implementacji usługi <xref:System.Transactions.TransactionScope> wystąpienie i użyj odpowiedniej wartości od <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrowanie usług dla przedsiębiorstw z operacji usługi  
 Poniższy przykład demonstruje operacji z dozwolone przepływu transakcji, która tworzy <xref:System.Transactions.TransactionScope> z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opcji. W tym scenariuszu mają zastosowanie następujące warunki:  
  
- Jeśli klient przepływu transakcji, działań, włącznie z wywołania do składnika usług dla przedsiębiorstw jest wykonywana w zakresie danej transakcji. Za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest zsynchronizowany z <xref:System.EnterpriseServices> kontekstu, co oznacza, że transakcja otoczenia <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.  
  
- Jeśli klient nie przepływu transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> do `true` tworzy nowy zakres transakcji dla tej operacji. Podobnie za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że operacji transakcji jest taki sam jak transakcji używana wewnątrz <xref:System.EnterpriseServices> kontekście składnika.  
  
 Wszelkie wywołania dodatkową metodę również występować w zakresie tej samej operacji transakcji.  
  
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
  
 Jeśli synchronizacja nie jest wymagany między operacji bieżącej transakcji i wywołania składników transakcyjnych usług dla przedsiębiorstw, należy użyć <xref:System.Transactions.EnterpriseServicesInteropOption.None> opcji podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrowanie usług dla przedsiębiorstw przy użyciu klienta  
 Poniższy przykład demonstruje klienta kodu za pomocą <xref:System.Transactions.TransactionScope> wystąpienia z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ustawienie. W tym scenariuszu wywołania operacji usługi, które obsługują przepływu transakcji występują w zakresie tej samej transakcji wywołania metody składniki usług dla przedsiębiorstw.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Współdziałanie z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
