---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: af6c2d726b03fe82f5447bdec25944149b966f2a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938070"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
Usługa WCF obsługuje Serializowanie danych w formacie JSON. W tym temacie opisano sposób, w jaki program WCF może serializować typy przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programowanie wiadomości z określonym typem  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jest używany, gdy <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany do operacji usługi. Oba te atrybuty umożliwiają określenie `RequestFormat` i `ResponseFormat`. Aby używać formatu JSON dla żądań i odpowiedzi. Ustaw obie te wartości, aby `WebMessageFormat.Json`.  Aby można było użyć JSON, należy użyć <xref:System.ServiceModel.WebHttpBinding>, która automatycznie konfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>. Aby uzyskać więcej informacji na temat serializacji WCF, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Aby uzyskać więcej informacji na temat JSON i WCF, zobacz [Service Station-Introduction to the RESTful Services with WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> Użycie formatu JSON wymaga użycia <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>, które nie obsługują komunikacji SOAP. Usługi, które komunikują się z <xref:System.ServiceModel.WebHttpBinding> nie obsługują ujawniania metadanych usługi, dzięki czemu nie będzie można używać funkcji Dodaj odwołanie do usługi programu Visual Studio lub narzędzia wiersza polecenia Svcutil w celu wygenerowania serwera proxy po stronie klienta. Aby uzyskać więcej informacji na temat programistycznego wywoływania usług korzystających z <xref:System.ServiceModel.WebHttpBinding>, zobacz [jak korzystać z usług REST w programie WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Programowanie komunikatów niewpisanych  
 Podczas pracy bezpośrednio z niewpisanymi obiektami komunikatów należy jawnie ustawić właściwości niewpisanej wiadomości, aby serializować ją jako kod JSON. Poniższy fragment kodu przedstawia, jak to zrobić.  
  
```csharp
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
