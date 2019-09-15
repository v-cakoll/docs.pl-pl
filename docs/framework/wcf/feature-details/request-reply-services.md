---
title: Usługi „żądanie-odpowiedź”
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991140"
---
# <a name="request-reply-services"></a>Usługi „żądanie-odpowiedź”
Usługi żądanie-odpowiedź są domyślnym typem kontraktu operacji w Windows Communication Foundation (WCF). Klienci podejmują wywołania do operacji usługi i oczekują na odpowiedź z usługi. Można wykonywać wywołania operacji usługi synchronicznie, gdzie klient jest blokowany do momentu odebrania odpowiedzi z usługi lub czasu wywołania lub asynchronicznego, gdzie klient wykonuje wywołanie do operacji usługi, kontynuuje pracę i odbiera Odpowiedź usługi w innym wątku.  
  
 Aby utworzyć kontrakt usługi żądanie-odpowiedź, zdefiniuj kontrakt usługi i Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Nie trzeba ustawiać <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości na `false` , ponieważ jest to zachowanie domyślne.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi jednokierunkowe](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
