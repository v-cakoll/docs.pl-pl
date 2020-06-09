---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: b5f0f730f90227dcccc7e5ebf533d80a28f6e6eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599298"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Tworzenie usług AJAX WCF bez platformy ASP.NET
Usługi Windows Communication Foundation (WCF) AJAX są dostępne z dowolnej strony sieci Web z obsługą języka JavaScript, bez konieczności ASP.NET AJAX. W tym temacie opisano sposób tworzenia takiej usługi WCF.  
  
 Aby uzyskać instrukcje dotyczące korzystania z programu WCF z ASP.NET AJAX, zobacz [Tworzenie usług WCF dla ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).  
  
 Istnieją trzy części do tworzenia usługi WCF AJAX:  
  
- Tworzenie punktu końcowego AJAX, do którego można uzyskać dostęp za pomocą przeglądarki.  
  
- Tworzenie kontraktu usługi zgodnej ze standardem AJAX.  
  
- Uzyskiwanie dostępu do usług WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Tworzenie punktu końcowego AJAX  
 Najbardziej podstawowym sposobem na włączenie obsługi technologii AJAX w usłudze WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> pliku w formacie SVC skojarzonym z usługą, jak w poniższym przykładzie.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatywnie można również użyć konfiguracji, aby dodać punkt końcowy AJAX. Użyj <xref:System.ServiceModel.WebHttpBinding> w punkcie końcowym usługi i skonfiguruj ten punkt końcowy przy użyciu <xref:System.ServiceModel.Description.WebHttpBehavior> tak jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX z danymi JSON i XML](../samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Tworzenie kontraktu usługi zgodnej ze standardem AJAX  
 Domyślnie kontrakty usługi udostępniane za pośrednictwem punktu końcowego AJAX zwracają dane w formacie XML. Ponadto domyślnie operacje usługi są dostępne za pośrednictwem żądań HTTP POST do adresów URL, które zawierają adres punktu końcowego, a następnie nazwę operacji, jak pokazano w poniższym przykładzie.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Ta operacja jest dostępna za pomocą polecenia POST protokołu HTTP w celu `http://serviceaddress/endpointaddress/GetCities` zwrócenia wiadomości XML.  
  
 Aby dostosować te podstawowe aspekty, można użyć pełnego modelu programowania sieci Web. Na przykład można użyć <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów lub, <xref:System.ServiceModel.Web.WebInvokeAttribute> Aby kontrolować czasownik http, do którego operacja reaguje, lub użyć `UriTemplate` właściwości tych atrybutów, aby określić niestandardowe identyfikatory URI. Aby uzyskać więcej informacji, zobacz temat [model programowania HTTP sieci Web](wcf-web-http-programming-model.md) w programie WCF.  
  
 Format danych JSON jest często używany w usługach AJAX. Aby utworzyć operację zwracającą kod JSON zamiast XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> Właściwość (lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> ) na <xref:System.ServiceModel.Web.WebMessageFormat.Json> . W temacie [autonomiczna Serializacja kodu JSON](stand-alone-json-serialization.md) pokazano, jak wbudowane typy .NET i typy kontraktów danych są mapowane na format JSON.  
  
 Zwykle żądania JSON i odpowiedzi składają się tylko z jednego elementu. Dla poprzedniej `GetCities` operacji żądanie jest podobne do następującej.  
  
```json
"na"  
```  
  
 Odpowiedź na to żądanie jest podobna do następującej.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Jeśli operacja przyjmuje dodatkowy parametr, styl żądania musi być opakowany, aby otoczyć oba parametry pojedynczym obiektem JSON. Przykład tego komunikatu JSON w stylu znajduje się w poniższym przykładzie.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Następujący kontrakt akceptuje tę wiadomość.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Uzyskiwanie dostępu do usług AJAX  
 Punkty końcowe AJAX programu WCF zawsze akceptują zarówno żądania JSON, jak i XML.  
  
 Żądania POST protokołu HTTP z typem zawartości "Application/JSON" są traktowane jako dane JSON oraz z typem zawartości, który wskazuje na XML (na przykład "text/xml"), są traktowane jako XML.  
  
 Żądania HTTP GET zawierają wszystkie parametry żądania w samym adresie URL.  
  
 Użytkownik może zdecydować, jak utworzyć żądanie HTTP do punktu końcowego. Ponadto użytkownik ma pełną kontrolę nad konstruowaniem kodu JSON, który stanowi treść żądania. Aby zapoznać się z przykładem tworzenia żądania w języku JavaScript, zobacz [usługę AJAX z danymi JSON i XML](../samples/ajax-service-with-json-and-xml-sample.md).
