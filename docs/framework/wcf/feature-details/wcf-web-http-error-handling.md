---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 34912bccaefb645541f47d083c5c307b20ff77c5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975953"
---
# <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF
Obsługa błędów HTTP sieci Web w programie Windows Communication Foundation (WCF) umożliwia zwracanie błędów z usług HTTP sieci Web w programie WCF, które określają kod stanu HTTP i zwracają szczegóły błędu przy użyciu tego samego formatu co operacja (na przykład XML lub JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF  
 Klasa <xref:System.ServiceModel.Web.WebFaultException> definiuje konstruktora, który umożliwia określenie kodu stanu HTTP. Ten kod stanu jest następnie zwracany do klienta. Ogólna wersja klasy <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601> umożliwia zwrócenie typu zdefiniowanego przez użytkownika, który zawiera informacje o błędzie, który wystąpił. Ten obiekt niestandardowy jest serializowany przy użyciu formatu określonego przez operację i zwracany do klienta. Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP i dodatkowe informacje w typie zdefiniowanym przez użytkownika. `MyErrorDetail` jest typem zdefiniowanym przez użytkownika, który zawiera dodatkowe informacje o błędzie, który wystąpił.  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Poprzedni kod zwraca odpowiedź HTTP z niedozwolonym kodem stanu i treścią zawierającą wystąpienie obiektu `MyErrorDetails`. Format obiektu `MyErrorDetails` jest określany na podstawie:  
  
- Wartość parametru `ResponseFormat` atrybutu <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> określonego w operacji usługi.  
  
- Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
- Wartość właściwości <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> przez uzyskanie dostępu do <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Aby uzyskać więcej informacji o tym, jak te wartości wpływają na formatowanie operacji, zobacz temat [Formatowanie http sieci Web](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.  
  
 <xref:System.ServiceModel.Web.WebFaultException> jest <xref:System.ServiceModel.FaultException> i dlatego może służyć jako model programowania wyjątków błędów dla usług, które uwidaczniają punkty końcowe protokołu SOAP, a także punkty końcowe HTTP sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Formatowanie kodu HTTP dla sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Definiowanie i określanie błędów](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
