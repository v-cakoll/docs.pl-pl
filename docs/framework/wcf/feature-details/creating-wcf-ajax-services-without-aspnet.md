---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857210"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Tworzenie usług AJAX WCF bez platformy ASP.NET
Usług AJAX Windows Communication Foundation (WCF) są dostępne w stronach sieci Web z obsługą języka JavaScript bez konieczności ASP.NET AJAX. W tym temacie opisano sposób tworzenia usługi WCF.  
  
 Aby uzyskać instrukcje na temat korzystania z usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [tworzenie usług WCF w technologii ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Istnieją trzy części do tworzenie usług WCF AJAX:  
  
- Tworzenie punktu końcowego AJAX, który jest możliwy za pomocą przeglądarki.  
  
- Tworzenie kontraktu usługi zgodne z technologii AJAX.  
  
- Uzyskiwanie dostępu do usług WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Tworzenie punktu końcowego AJAX  
 Najbardziej podstawową metodą, aby włączyć obsługę technologii AJAX w usłudze WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> w pliku svc skojarzonego z usługą, jak w poniższym przykładzie.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatywnie umożliwia także konfigurację Dodawanie punktu końcowego AJAX. Użyj <xref:System.ServiceModel.WebHttpBinding> w punkcie końcowym usługi i skonfigurować punkt końcowy z <xref:System.ServiceModel.Description.WebHttpBehavior> jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Aby uzyskać przykład pracy, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Tworzenie kontraktu usługi zgodne z technologii AJAX  
 Domyślnie kontraktów usług udostępnianych za pośrednictwem danych zwrotnych punktu końcowego AJAX w formacie XML. Domyślnie operacje usług są także dostępne za pośrednictwem żądania HTTP POST do adresów URL, które obejmują adres punktu końcowego, a następnie według nazwy operacji, jak pokazano w poniższym przykładzie.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Ta operacja jest dostępny za pośrednictwem metody POST protokołu HTTP do `http://serviceaddress/endpointaddress/GetCities` i zwrócić komunikat XML.  
  
 Pełny Model programowania sieci Web umożliwia dostosowanie tych właściwości podstawowe. Na przykład, można użyć <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty kontrolować zlecenie HTTP, na które odpowiada operację lub użyj `UriTemplate` właściwości tych odpowiednich atrybutów, aby określić niestandardowe identyfikatory URI. Aby uzyskać więcej informacji, zobacz [modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tematu.  
  
 Format danych JSON jest często używane w usługach AJAX. Aby utworzyć operację zwracającą JSON zamiast XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) właściwość <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Serializacji JSON autonomicznego](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) temacie pokazano, jak wbudowana .NET typów i danych kontraktu typów mapy do formatu JSON.  
  
 Normalnie JSON, żądań i odpowiedzi zawierają tylko jeden element. Do poprzedniego `GetCities` operację żądania przypomina następującą instrukcję.  
  
```  
"na"  
```  
  
 Odpowiedź na to żądanie przypomina następującą instrukcję.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Jeśli operacja zajmuje dodatkowy parametr, styl żądania muszą być zapakowane do opakowania oba parametry w pojedynczy obiekt JSON. Przykładowy komunikat JSON ten styl jest w poniższym przykładzie.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Następujące umowy akceptuje tej wiadomości.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Uzyskiwanie dostępu do usług AJAX  
 Punktów końcowych WCF AJAX zawsze akceptować żądania JSON i XML.  
  
 Żądania HTTP POST z typem zawartości "application/json" są traktowane jako dane JSON, a te o typie zawartości, wskazujące XML (na przykład "text/xml") są traktowane jako XML.  
  
 Żądania HTTP GET zawiera wszystkie parametry żądania w adresie URL, sam.  
  
 Jest użytkownika o decyzję, jak utworzyć żądanie HTTP do punktu końcowego. Ponadto użytkownik ma pełną kontrolę nad konstruowanie JSON, który wchodzi w skład treści żądania. Aby uzyskać przykład tworzenia żądania poziomu języka JavaScript, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
