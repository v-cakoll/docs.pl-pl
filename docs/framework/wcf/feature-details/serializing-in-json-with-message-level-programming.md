---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 6e8bb43b7a7755c20699aa377c9d60b0f285493b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949202"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
Usługa WCF obsługuje Serializowanie danych w formacie JSON. W tym temacie opisano sposób, w jaki program WCF może serializować typy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>przy użyciu.  
  
## <a name="typed-message-programming"></a>Programowanie wiadomości z określonym typem  
 Jest <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używany, <xref:System.ServiceModel.Web.WebGetAttribute> gdy lub <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany do operacji usługi. Oba te atrybuty umożliwiają określenie `RequestFormat` i. `ResponseFormat` Aby używać formatu JSON dla żądań i odpowiedzi. Ustaw obie te wartości na `WebMessageFormat.Json`.  Aby można było użyć formatu JSON, należy użyć <xref:System.ServiceModel.WebHttpBinding>, który automatycznie <xref:System.ServiceModel.Description.WebHttpBehavior>konfiguruje. Aby uzyskać więcej informacji na temat serializacji WCF, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Aby uzyskać więcej informacji na temat JSON i WCF, zobacz [Service Station-Introduction to the RESTful Services with WCF](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
> Użycie formatu JSON wymaga użycia <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> , które nie obsługują komunikacji SOAP. Usługi, które komunikują <xref:System.ServiceModel.WebHttpBinding> się z nieobsługiwanymi metadanymi usługi, dzięki czemu nie będzie można używać funkcji Dodaj odwołanie do usługi programu Visual Studio lub narzędzia wiersza polecenia Svcutil do generowania serwera proxy po stronie klienta. Aby uzyskać więcej informacji na temat programistycznego wywoływania usług, <xref:System.ServiceModel.WebHttpBinding>które są używane, zobacz [jak korzystać z usług REST w programie WCF](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programowanie komunikatów niewpisanych  
 Podczas pracy bezpośrednio z niewpisanymi obiektami komunikatów należy jawnie ustawić właściwości niewpisanej wiadomości, aby serializować ją jako kod JSON. Poniższy fragment kodu przedstawia, jak to zrobić.  
  
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
