---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="request-reply-services"></a>Usługi „żądanie-odpowiedź”
Usługi "żądanie-odpowiedź" są domyślny typ kontrakt operacji w systemie Windows Communication Foundation (WCF). Klienci wykonywania wywołań do operacji usługi i oczekiwania na odpowiedź z usługi. Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klient blokuje aż do jej odbiera odpowiedź z usługi lub razy wywołania lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.  
  
 Aby utworzyć kontrakt usługi "żądanie-odpowiedź", zdefiniuj dany kontrakt usługi i zastosować <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, jak pokazano w poniższym kodzie próbki.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Nie trzeba ustawić <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `false` , ponieważ jest to zachowanie domyślne.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi jednokierunkowe](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
