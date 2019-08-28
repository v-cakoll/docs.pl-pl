---
title: Tworzenie usług WCF w technologii AJAX na platformie ASP.NET
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 64be5c8ec0d3ee105e026794912a9820bd7892d0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045965"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Tworzenie usług WCF w technologii AJAX na platformie ASP.NET

Microsoft ASP.NET AJAX umożliwia szybkie tworzenie stron sieci Web, które zawierają rozbudowane środowisko użytkownika, dzięki czemu odpowiadają i dobrze znane elementy interfejsu użytkownika. ASP.NET AJAX udostępnia biblioteki skryptów klienta, które obejmują technologię języka ECMAScript (JavaScript) dla wielu przeglądarek i dynamiczne technologie HTML (DHTML) i integrują je z platformą deweloperskią opartą na serwerze ASP.NET 2,0. Za pomocą ASP.NET AJAX można poprawić środowisko użytkownika i wydajność aplikacji sieci Web.

ASP.NET AJAX składa się z bibliotek skryptów klienta i składników serwera, które są zintegrowane w celu zapewnienia niezawodnej struktury programistycznej. Aby uzyskać dostęp do usługi ze strony ASP.NET: po dodaniu adresu URL usługi do kontrolki Menedżera skryptów ASP.NET na stronie operacje usługi mogą być wywoływane przy użyciu kodu JavaScript, który wygląda tak samo jak zwykłe wywołanie funkcji JavaScript. Zobacz [naucz ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) o korzystaniu z usług sieci Web w ramach platformy AJAX.

Większość usług Windows Communication Foundation (WCF) może być narażonych jako usługa zgodna z ASP.NET AJAX przez dodanie odpowiedniego punktu końcowego ASP.NET AJAX.

Jeśli używasz programu Visual Studio, możesz użyć wstępnie skompilowanego szablonu dla usług WCF z włączoną obsługą technologii AJAX, który jest dostępny w oknie dialogowym **Dodaj nowy element** podczas pracy z witrynami sieci Web ASP.NET lub aplikacjami sieci Web.

Jeśli nie korzystasz z szablonów programu Visual Studio, istnieją dwa sposoby tworzenia punktu końcowego ASP.NET AJAX:

- Utwórz punkt końcowy przy użyciu aktywacji hosta dynamicznego bez użycia żadnej konfiguracji. Jest to najbardziej podstawowe podejście, jeśli nie znasz systemu konfiguracji WCF. Aby uzyskać więcej informacji, zobacz [jak: Dodaj punkt końcowy ASP.NET AJAX bez użycia opcji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)Configuration.

- Dodaj punkt końcowy z obsługą technologii AJAX do usługi WCF przy użyciu konfiguracji. Aby uzyskać więcej informacji, zobacz [jak: Użyj konfiguracji, aby dodać punkt końcowy](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.

Model programowania sieci Web opisany w temacie [Omówienie modelu programowania HTTP sieci Web](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) w programie WCF może być używany z usługami ASP.NET AJAX. Opracowany

- Można użyć <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów i <xref:System.ServiceModel.Web.WebInvokeAttribute> , aby wybrać między czasownikami HTTP GET i http post. Jeśli są używane prawidłowo, może to znacząco poprawić wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Wybierz między żądaniami HTTP POST i HTTP GET dla punktów końcowych](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)ASP.NET AJAX.

- Możesz użyć <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> właściwości i <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> , aby spowodować, że usługa zwróci dane XML zamiast domyślnego JavaScript Object Notation (JSON). W tym celu ASP.NET AJAX Framework powoduje, że klient JavaScript otrzymuje obiekt XML DOM.

  > [!WARNING]
  > Aby to działało, w operacji musi być ustawiony typ zawartości text/xml. W przeciwnym razie klient JavaScript otrzyma ciąg zawierający kod XML zamiast obiektu DOM XML.

    Poniżej przedstawiono przykład operacji zwracającej dane XML z ustawionym odpowiednio typem zawartości:

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- Nie można zmienić innych właściwości <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów <xref:System.ServiceModel.Web.WebInvokeAttribute> i, jeśli jest wymagana zgodność z ASP.NET AJAX. Inne aspekty modelu programowania sieci Web mogą być używane tak długo, jak konwencje wywołań AJAX ASP.NET nie są naruszane.

 Bardziej zaawansowane scenariusze wymagają zrozumienia dodatkowych informacji o obsłudze AJAX w programie WCF:

- Aby zrozumieć, w jaki sposób dane są przesyłane między klientem strony AJAX a usługą WCF przy użyciu języka JavaScript, i aby uzyskać szczegółowe informacje na temat tego, jak typy .NET Framework są mapowane na typy JavaScript, zobacz [Obsługa formatu JSON i innych formatów transfer danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).

- Aby korzystać z funkcji ASP.NET, na przykład uwierzytelniania opartego na adresach URL i uzyskiwania dostępu do informacji o sesji ASP.NET, można włączyć tryb zgodności ASP.NET za pomocą konfiguracji.

Punkty końcowe AJAX w WCF mogą nawet być używane bez ASP.NET AJAX Framework. W ten sposób należy zrozumieć architekturę pomocy technicznej AJAX w programie WCF. Aby zapoznać się z omówieniem tej architektury, zobacz [model obiektów programowania HTTP sieci Web](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)w programie WCF. Aby uzyskać przykładowy kod ilustrujący takie podejście, zobacz [usługi AJAX z danymi JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Instrukcje: Dodaj punkt końcowy ASP.NET AJAX bez używania konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Instrukcje: Użyj konfiguracji, aby dodać punkt końcowy ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
