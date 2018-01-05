---
title: "Usługi „żądanie-odpowiedź”"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e8c01fa3451cbeb335c4771e287566af1c104b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-services"></a>Usługi „żądanie-odpowiedź”
Usługi "żądanie-odpowiedź" to domyślny typ kontrakt operacji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Klienci wykonywania wywołań do operacji usługi i oczekiwania na odpowiedź z usługi. Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klient blokuje aż do jej odbiera odpowiedź z usługi lub razy wywołania lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.  
  
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
