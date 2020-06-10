---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: b1d41bebafa2795d390b120ad84475417389479b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598648"
---
# <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF
Obsługa błędów HTTP sieci Web w programie Windows Communication Foundation (WCF) umożliwia zwracanie błędów z usług HTTP sieci Web w programie WCF, które określają kod stanu HTTP i zwracają szczegóły błędu przy użyciu tego samego formatu co operacja (na przykład XML lub JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF  
 <xref:System.ServiceModel.Web.WebFaultException>Klasa definiuje konstruktora, który umożliwia określenie kodu stanu HTTP. Ten kod stanu jest następnie zwracany do klienta. Ogólna wersja <xref:System.ServiceModel.Web.WebFaultException> klasy, <xref:System.ServiceModel.Web.WebFaultException%601> umożliwia zwrócenie typu zdefiniowanego przez użytkownika, który zawiera informacje o błędzie, który wystąpił. Ten obiekt niestandardowy jest serializowany przy użyciu formatu określonego przez operację i zwracany do klienta. Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP i dodatkowe informacje w typie zdefiniowanym przez użytkownika. `MyErrorDetail`jest typem zdefiniowanym przez użytkownika, który zawiera dodatkowe informacje o błędzie, który wystąpił.  
  
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
  
 Poprzedni kod zwraca odpowiedź HTTP z niedozwolonym kodem stanu i treścią zawierającą wystąpienie `MyErrorDetails` obiektu. Format `MyErrorDetails` obiektu jest określany przez:  
  
- Wartość `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu określonego w operacji usługi.  
  
- Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .  
  
- Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Właściwości przez uzyskanie dostępu do elementu <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .  
  
 Aby uzyskać więcej informacji o tym, jak te wartości wpływają na formatowanie operacji, zobacz temat [Formatowanie http sieci Web](wcf-web-http-formatting.md)w programie WCF.  
  
 <xref:System.ServiceModel.Web.WebFaultException>jest <xref:System.ServiceModel.FaultException> i dlatego może służyć jako model programowania wyjątku błędów dla usług, które uwidaczniają punkty końcowe protokołu SOAP, a także punkty końcowe http sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
- [Formatowanie kodu HTTP dla sieci Web w programie WCF](wcf-web-http-formatting.md)
- [Definiowanie i określanie błędów](../defining-and-specifying-faults.md)
- [Obsługa wyjątków i błędów](../extending/handling-exceptions-and-faults.md)
- [Wysyłanie i odbieranie błędów](../sending-and-receiving-faults.md)
