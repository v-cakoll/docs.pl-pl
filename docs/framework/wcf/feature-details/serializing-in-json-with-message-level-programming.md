---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: fc2777d71376cc482b715898fa81ddf618bd8284
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186943"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
Usługi WCF obsługuje serializacji danych w formacie JSON. W tym temacie opisano, jak sprawdzić WCF do serializacji typów przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programowanie wpisany komunikat  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jest używane podczas <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany do operacji usługi. Oba te atrybuty pozwalają na określenie `RequestFormat` i `ResponseFormat`. Aby użyć formatu JSON dla żądań i odpowiedzi. oba te można ustawić `WebMessageFormat.Json`.  Aby można było używać JSON, należy użyć <xref:System.ServiceModel.WebHttpBinding>, która automatycznie konfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>. Aby uzyskać więcej informacji na temat serializacji WCF zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Aby uzyskać więcej informacji na temat formatu JSON i WCF, zobacz [stacja usługi — wprowadzenie do RESTful usług przy użyciu programu WCF](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
>  Przy użyciu wymaga użycia <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> nie obsługują komunikację protokołu SOAP. Usługi, które komunikują się z <xref:System.ServiceModel.WebHttpBinding> nie obsługują metadanych narażając konta usługi, więc nie można użyć funkcji Dodaj odwołanie do usługi Visual Studio lub narzędzia wiersza polecenia narzędzia svcutil do generowania serwera proxy po stronie klienta. Aby uzyskać więcej informacji, w jaki sposób można programowo wywołać usługi używające <xref:System.ServiceModel.WebHttpBinding>, zobacz [używanie usług REST z usługą WCF](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Komunikat bez programowania  
 Podczas pracy bezpośrednio z obiektów bez typu komunikatu, musisz jawnie ustawić właściwości na komunikat bez typu, który ma serializować go jako plik JSON. Poniższy fragment kodu pokazuje, jak to zrobić.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa integracji AJAX i notacji JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serializacja JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
