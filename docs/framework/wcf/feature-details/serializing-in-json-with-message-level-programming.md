---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 33337f75032031ccfc81173f188f4ff7695ffd40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
Usługi WCF obsługuje serializacji danych w formacie JSON. W tym temacie opisano, jak sprawdzić WCF do serializacji z typów, za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Wpisany komunikat programowania  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Służy po <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany do operacji usługi. Oba te atrybuty umożliwiają określenie `RequestFormat` i `ResponseFormat`. Aby używać JSON dla żądań i odpowiedzi Ustaw oba te do `WebMessageFormat.Json`.  Aby można było używać JSON, należy użyć <xref:System.ServiceModel.WebHttpBinding> którego automatycznie konfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>. Aby uzyskać więcej informacji na temat serializacji WCF, zobacz: [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [szeregowanie programu Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx). Aby uzyskać więcej informacji na temat formatu JSON i WCF zobacz [wprowadzenie do usług RESTfull z programem WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [włączone JSON tworzenie usług WCF w .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), i [omówienie REST w programie WCF](http://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  Przy użyciu wymaga użycia <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> nie obsługują komunikację protokołu SOAP. Usługi, które komunikują się z <xref:System.ServiceModel.WebHttpBinding> nie obsługują uwidaczniającą metadanych usługi, więc nie można wygenerować serwer proxy po stronie klienta za pomocą funkcji Dodaj odwołanie do usługi Visual Studio lub narzędzie wiersza polecenia narzędzia svcutil. Aby uzyskać więcej informacji, jak programowo można wywołać usługi używające <xref:System.ServiceModel.WebHttpBinding>, zobacz [jak korzystać z usługi REST z programem WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programowanie komunikat bez typu  
 Podczas pracy bezpośrednio z obiektów komunikat bez typu, musisz jawnie ustawić właściwości na komunikat bez do serializacji go w formacie JSON. Poniższy fragment kodu pokazano, jak to zrobić.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Integracji AJAX i obsługi JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Serializacja JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
