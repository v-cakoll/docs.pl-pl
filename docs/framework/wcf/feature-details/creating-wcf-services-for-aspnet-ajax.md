---
title: Tworzenie usług WCF w technologii AJAX na platformie ASP.NET
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 4d3953046a796686a465cd8096b8f2ba930aa9fd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536654"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Tworzenie usług WCF w technologii AJAX na platformie ASP.NET
Microsoft ASP.NET AJAX umożliwia szybkie tworzenie strony sieci Web, które zawierają zaawansowany interfejs użytkownika przy użyciu elementów interfejsu użytkownika dynamiczne i dobrze znane. ASP.NET AJAX udostępnia biblioteki skryptu klienta, obejmujące przeglądarek ECMAScript (JavaScript) i dynamiczny technologii HTML (DHTML) i integruje się je z platform programistycznych opartych na serwerze programu ASP.NET 2.0. Za pomocą kodu ASP.NET AJAX, możesz poprawić środowisko użytkownika i wydajność aplikacji sieci Web.  
  
 ASP.NET AJAX składa się z bibliotek skryptu klienta i składniki serwera, które są zintegrowane platforma tworzenia niezawodnych. Dostęp do usługi ze strony programu ASP.NET: po dodaniu adresu URL usługi do kontrolki Menedżera skryptów platformy ASP.NET na stronie Operacje usług mogą być wywoływane przy użyciu kodu JavaScript, który wygląda tak samo jak regularne wywołanie funkcji JavaScript. Zobacz [Dowiedz się, ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) dotyczące korzystania z usług sieci Web w ramach technologii AJAX.  
  
 Większość usług Windows Communication Foundation (WCF) może być udostępniany jako usługa zgodny z ASP.NET AJAX przez dodanie odpowiednich punktów końcowych ASP.NET AJAX.  
  
 Jeśli w programie Visual Studio można użyć wstępnie utworzonego szablonu dla usługi WCF z włączoną obsługą technologii AJAX, dostępne w **Dodaj nowy element** okno dialogowe podczas pracy z witryn sieci Web platformy ASP.NET lub aplikacji sieci Web.  
  
 Jeśli nie używasz szablony programu Visual Studio, istnieją dwa sposoby tworzenia punktu końcowego ASP.NET AJAX:  
  
-   Tworzenie punktu końcowego, bez używania żadnej konfiguracji przy użyciu aktywacji hosta dynamicznego. Jest to najbardziej podstawowa metoda, jeśli znasz system konfiguracji usługi WCF. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie platformy ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Dodaj punkt końcowy z włączoną obsługą technologii AJAX do usługi WCF, za pomocą konfiguracji. Aby uzyskać więcej informacji, zobacz [porady: Użyj konfiguracji, aby dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Model programowania sieci Web, które są opisane w [Programming Overview modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) może być używany z usługami ASP.NET AJAX. W szczególności:  
  
-   Możesz użyć <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów, aby wybrać zleceń HTTP GET i POST protokołu HTTP. Jeśli są prawidłowo wykorzystywane to znacznie poprawić wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie między żądania HTTP POST i HTTP GET żądań dla punktów końcowych AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Możesz użyć <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> i <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości, aby spowodować, że usługi zwrócić dane XML zamiast domyślnego języka JavaScript Object Notation (JSON). W ten sposób za pomocą programu ASP.NET AJAX framework powoduje, że klient JavaScript otrzymać obiekt modelu DOM języka XML.  
  
    > [!WARNING]
    >  Operacja musi Ustaw typ zawartości tekstu/xml, aby to działało. W przeciwnym razie klienta JavaScript zostanie wyświetlony ciąg zawierający XML zamiast obiektu modelu DOM języka XML.  
  
     Oto przykład operacja, która zwraca dane XML z typu zawartości, odpowiednio ustawić:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Nie inne właściwości w <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty można zmienić, jeśli wymagana jest zgodność z ASP.NET AJAX. Inne aspekty w sieci Web w modelu programowania można tak długo, jak nie naruszenia konwencji wywoływania ASP.NET AJAX.  
  
 Bardziej zaawansowanych scenariuszy wymagają zrozumienie niektóre dodatkowe szczegóły Obsługa technologii AJAX w programie WCF:  
  
-   Aby dowiedzieć się, jak dane są przesyłane między klientem strony AJAX i usługi WCF przy użyciu języka JavaScript oraz szczegółowe informacje w sposób mapowania typów programu .NET Framework do typów języka JavaScript, zobacz [obsługi formatu JSON oraz inne formaty transferu danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   Aby móc korzystać z funkcji programu ASP.NET, na przykład uwierzytelniania opartego na adresach URL i uzyskiwania dostępu do informacji o sesji programu ASP.NET, warto włączyć tryb zgodności ASP.NET za pomocą konfiguracji.  
  
 Punktów końcowych AJAX w programie WCF nawet może być używane bez framework ASP.NET AJAX. Wymaga zrozumienia architektury pomocy technicznej Obsługa technologii AJAX w programie WCF. Omówienie tej architektury, zobacz [programowania modelu obiektu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Dla przykładu kodu, demonstrując tej metody, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Instrukcje: wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
