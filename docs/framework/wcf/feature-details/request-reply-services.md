---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: a8d9ee30df5198335b15d2d7130d853f4dd73a18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516658"
---
# <a name="request-reply-services"></a>Usługi „żądanie-odpowiedź”
Usługi "żądanie-odpowiedź" to typ domyślny kontrakt operacji w Windows Communication Foundation (WCF). Klienci wykonywanie wywołań do operacji usługi i oczekiwania na odpowiedź z usługi. Można wykonywać wywołania operacji usługi albo synchronicznie, w przypadku, gdy klienta blokuje aż do jego odbiera odpowiedź od usługi lub czasy wywołań lub asynchronicznie, gdy klient wysyła wywołania operacji usługi kontynuuje współpracę i odbiera odpowiedź z usługi w innym wątku.  
  
 Aby utworzyć kontrakt usługi "żądanie-odpowiedź", definiowanie kontraktu usługi, usługi i zastosować <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, jak pokazano w poniższym przykładowym kodzie.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Nie trzeba ustawić <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `false` , ponieważ jest to zachowanie domyślne.  
  
## <a name="see-also"></a>Zobacz także
- [Usługi jednokierunkowe](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
