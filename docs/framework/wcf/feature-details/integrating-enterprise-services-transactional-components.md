---
title: "Integrowanie składników transakcyjnych usług dla przedsiębiorstw"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a236a34dd20661d62d59a3712a1800ff1f9a11ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a>Integrowanie składników transakcyjnych usług dla przedsiębiorstw
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]udostępnia mechanizm automatycznego do integracji z usługami przedsiębiorstwa (zobacz [współdziałanie z aplikacjami COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Może być jednak elastyczność tworzenia usług używających wewnętrznie składników transakcyjnych hostowanych w ramach usług dla przedsiębiorstw. Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcji transakcji jest oparty na <xref:System.Transactions> infrastruktury, proces Integrowanie usług dla przedsiębiorstw o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest identyczna jak służący do określania współdziałanie <xref:System.Transactions> i Enterprise Usługi w sposób opisany w [współdziałanie z usługami przedsiębiorstwa i transakcje COM +](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Aby zapewnić żądany poziom współdziałanie transakcji przychodzącej i transakcji kontekstu modelu COM +, należy utworzyć implementacji usługi <xref:System.Transactions.TransactionScope> wystąpienia i użyj odpowiednią wartość z <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Integrowanie usług dla przedsiębiorstw z operacji usługi  
 Poniższy kod przedstawia operacji z użyciem przepływu transakcji dozwolone, która tworzy <xref:System.Transactions.TransactionScope> z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> opcji. W tym scenariuszu mają zastosowanie następujące warunki:  
  
-   Jeśli klient przepływu transakcji, wykonaniem operacji, w tym wywołaniu składnika usług dla przedsiębiorstw w zakresie transakcji. Przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> gwarantuje, że transakcja jest zsynchronizowany z <xref:System.EnterpriseServices> kontekstu, co oznacza, że transakcja otoczenia dla <xref:System.Transactions> i <xref:System.EnterpriseServices> jest taka sama.  
  
-   Jeśli klient nie przepływu transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> do `true` tworzy nowy zakres transakcji dla tej operacji. Podobnie za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> zapewnia, że operacji transakcji jest taki sam, jak używać wewnątrz transakcji <xref:System.EnterpriseServices> kontekście składnika.  
  
 Wszystkie wywołania metody dodatkowe także wystąpić w zakresie transakcji tej samej operacji.  
  
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
  
 Jeśli synchronizacja nie jest wymagany między operacji bieżącej transakcji i wywołania składników transakcyjnych usług dla przedsiębiorstw, należy użyć <xref:System.Transactions.EnterpriseServicesInteropOption.None> podczas tworzenia wystąpienia <xref:System.Transactions.TransactionScope> wystąpienia.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Integrowanie usług dla przedsiębiorstw, za pomocą klienta  
 Poniższy kod przedstawia kodu klienta za pomocą <xref:System.Transactions.TransactionScope> wystąpienia z <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ustawienie. W tym scenariuszu wywołania do operacji usługi, które obsługują przepływu transakcji występuje w zakresie jednej transakcji wywołania metody składniki usług dla przedsiębiorstw.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z aplikacjami COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Współdziałanie z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
