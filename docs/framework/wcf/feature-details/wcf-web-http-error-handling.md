---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 834c642e36e1551081dbe1f14529ed7596df1360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152701"
---
# <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF
Obsługa błędów protokołu HTTP sieci Web Windows Communication Foundation (WCF) pozwala zwrócić błędy z usług WCF Web HTTP, które określić kod stanu HTTP i zwraca szczegóły błędu przy użyciu tego samego formatu co operacji (na przykład XML lub JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF  
 <xref:System.ServiceModel.Web.WebFaultException> Klasa definiuje konstruktora, który pozwala określić kod stanu HTTP. Ten kod stanu jest zwracany do klienta. Ogólny wersję <xref:System.ServiceModel.Web.WebFaultException> klasy <xref:System.ServiceModel.Web.WebFaultException%601> umożliwia zwracają typ zdefiniowany przez użytkownika, który zawiera informacje o błędzie, który wystąpił. Ten niestandardowy obiekt jest serializowany, przy użyciu formatu określony przez operację i zwracany do klienta. Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP i dodatkowe informacje w typ zdefiniowany przez użytkownika. `MyErrorDetail` jest typ zdefiniowany przez użytkownika, który zawiera dodatkowe informacje o błędzie, który wystąpił.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Powyższy kod zwraca odpowiedź HTTP z kodem stanu zabronione i treści, która zawiera wystąpienie `MyErrorDetails` obiektu. Format `MyErrorDetails` obiektu jest określana przez:  
  
-   Wartość `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu wskazanego w operacji usługi.  
  
-   Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwości, uzyskując dostęp do <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Aby uzyskać więcej informacji na temat wpływu tych wartości na formatowanie operacji, zobacz [WCF Web HTTP formatowanie](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> jest <xref:System.ServiceModel.FaultException> i dlatego może służyć jako model programowania wyjątków błędów dla usług, które uwidaczniają punkty końcowe protokołu SOAP, a także punktów końcowych HTTP w sieci web.  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Formatowanie kodu HTTP dla sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Definiowanie i określanie błędów](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
