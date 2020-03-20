---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184498"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
WCF obsługuje serializacji danych w formacie JSON. W tym temacie opisano sposób informowania WCF <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>o serializacji typów przy użyciu pliku .  
  
## <a name="typed-message-programming"></a>Programowanie wpisanych wiadomości  
 Jest <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używany, <xref:System.ServiceModel.Web.WebGetAttribute> gdy <xref:System.ServiceModel.Web.WebInvokeAttribute> lub jest stosowany do operacji usługi. Oba te atrybuty umożliwiają `RequestFormat` określenie `ResponseFormat`i . Aby użyć JSON dla żądań i odpowiedzi. ustawić oba te `WebMessageFormat.Json`elementy na .  Aby korzystać z JSON, <xref:System.ServiceModel.WebHttpBinding>należy użyć programu , <xref:System.ServiceModel.Description.WebHttpBehavior>który automatycznie konfiguruje plik . Aby uzyskać więcej informacji na temat serializacji WCF, zobacz [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Aby uzyskać więcej informacji na temat JSON i WCF, zobacz [Stacja serwisowa - Wprowadzenie do usług RESTful z WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> Korzystanie z JSON <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> wymaga użycia i które nie obsługują komunikacji PROTOKOŁU SOAP. Usługi, które <xref:System.ServiceModel.WebHttpBinding> komunikują się z nie obsługują uwidaczniania metadanych usługi, więc nie będzie można użyć funkcji Dodaj odwołanie do usługi programu Visual Studio lub narzędzia wiersza polecenia svcutil do generowania serwera proxy po stronie klienta. Aby uzyskać więcej informacji, jak programowo <xref:System.ServiceModel.WebHttpBinding>wywoływać usługi, które używają , zobacz [Jak korzystać z usług REST z WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Programowanie wiadomości bez typu  
 Podczas pracy bezpośrednio z untyped Message obiektów, należy jawnie ustawić właściwości w wiadomości bez typu, aby serializować go jako JSON. Poniższy fragment kodu pokazuje, jak to zrobić.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa integracji AJAX i notacji JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serializacja JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
