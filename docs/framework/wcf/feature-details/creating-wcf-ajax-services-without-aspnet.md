---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185237"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Tworzenie usług AJAX WCF bez platformy ASP.NET
Dostęp do usług Ajax (Windows Communication Foundation ( WCF) można uzyskać z dowolnej strony sieci Web obsługującej obsługę języka JavaScript, bez konieczności ASP.NET ajax. W tym temacie opisano sposób tworzenia takiej usługi WCF.  
  
 Aby uzyskać instrukcje dotyczące używania WCF z ASP.NET AJAX, zobacz [Tworzenie usług WCF dla ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Istnieją trzy części do tworzenia usługi WCF AJAX:  
  
- Tworzenie punktu końcowego AJAX, który można uzyskać z przeglądarki.  
  
- Tworzenie umowy serwisowej zgodnej z ajaxem.  
  
- Uzyskiwanie dostępu do usług WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Tworzenie punktu końcowego AJAX  
 Najbardziej podstawowym sposobem włączenia obsługi AJAX w usłudze WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> pliku .svc skojarzonego z usługą, jak w poniższym przykładzie.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatywnie można również użyć konfiguracji, aby dodać punkt końcowy AJAX. Użyj <xref:System.ServiceModel.WebHttpBinding> punktu końcowego usługi i skonfiguruj ten punkt końcowy z <xref:System.ServiceModel.Description.WebHttpBehavior> jak pokazano w poniższym urywek kodu.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Na przykład roboczy zobacz [usługę AJAX z JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Tworzenie umowy serwisowej zgodnej z ajaxem  
 Domyślnie umowy serwisowe udostępniane za pomocą punktu końcowego AJAX zwracają dane w formacie XML. Ponadto domyślne operacje usługi są dostępne za pośrednictwem żądań HTTP POST do adresów URL, które zawierają adres punktu końcowego, po którym następuje nazwa operacji, jak pokazano w poniższym przykładzie.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Ta operacja jest dostępna przy `http://serviceaddress/endpointaddress/GetCities` użyciu protokołu HTTP POST i zwraca komunikatu XML.  
  
 Aby dostosować te podstawowe aspekty, można użyć pełnego modelu programowania sieci Web. Na przykład można użyć <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów lub kontrolować zlecenie HTTP, na który `UriTemplate` odpowiada operacja lub użyć właściwości tych odpowiednich atrybutów, aby określić niestandardowe identyfikatory URI. Aby uzyskać więcej informacji, zobacz [WCF Web HTTP Model tematu.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
 Format danych JSON jest często używany w usługach AJAX. Aby utworzyć operację zwracaną JSON zamiast XML, <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> ustaw <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>właściwość <xref:System.ServiceModel.Web.WebMessageFormat.Json>(lub) na . W [temacie Samodzielna serializacja JSON przedstawiono,](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) jak wbudowane typy .NET i typy kontraktów danych są mapowane na JSON.  
  
 Zwykle żądania JSON i odpowiedzi składają się tylko z jednego elementu. Dla poprzedniej `GetCities` operacji żądanie przypomina następującą instrukcję.  
  
```json
"na"  
```  
  
 Odpowiedź na to żądanie przypomina następującą instrukcję.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Jeśli operacja przyjmuje dodatkowy parametr, styl żądania musi być zawinięty, aby zawinąć oba parametry w pojedynczym obiekcie JSON. Przykład tego stylu komunikat JSON znajduje się w poniższym przykładzie.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Poniższa umowa akceptuje ten komunikat.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Uzyskiwanie dostępu do usług AJAX  
 Punkty końcowe WCF AJAX zawsze akceptują żądania JSON i XML.  
  
 Żądania HTTP POST z typem zawartości "application/json" są traktowane jako JSON, a te z typem zawartości, które wskazują XML (na przykład "text/xml") są traktowane jako XML.  
  
 Żądania HTTP GET zawierają wszystkie parametry żądania w samym adresie URL.  
  
 To do użytkownika, aby zdecydować, jak utworzyć żądanie HTTP do punktu końcowego. Ponadto użytkownik ma pełną kontrolę nad konstruowania JSON, który tworzy treść żądania. Na przykład tworzenia żądania z języka JavaScript zobacz [usługę AJAX z JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
