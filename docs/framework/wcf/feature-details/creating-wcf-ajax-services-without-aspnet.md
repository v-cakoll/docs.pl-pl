---
title: Tworzenie usług AJAX WCF bez platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490360"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Tworzenie usług AJAX WCF bez platformy ASP.NET
Usług AJAX Windows Communication Foundation (WCF) są dostępne z dowolnej strony włączenia obsługi języka JavaScript sieci Web bez konieczności ASP.NET AJAX. W tym temacie opisano sposób tworzenia usługi WCF.  
  
 Aby uzyskać instrukcje dotyczące przy użyciu programu WCF z ASP.NET AJAX, zobacz [tworzenie usług WCF dla środowiska ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Istnieją trzy części Tworzenie usług WCF AJAX:  
  
-   Tworzenie punktu końcowego AJAX, które są dostępne w przeglądarce.  
  
-   Tworzenie AJAX zgodnego kontraktu usługi.  
  
-   Dostęp do usług WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Tworzenie punktu końcowego AJAX  
 Najprostszym sposobem włączenie obsługi technologii AJAX w usługi WCF jest użycie <xref:System.ServiceModel.Activation.WebServiceHostFactory> w pliku svc skojarzonego z usługą, jak w poniższym przykładzie.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternatywnie umożliwia także konfiguracji można dodać punktu końcowego AJAX. Użyj <xref:System.ServiceModel.WebHttpBinding> na punkt końcowy usługi i konfigurowania tego punktu końcowego z <xref:System.ServiceModel.Description.WebHttpBehavior> pokazane na poniższy fragment kodu.  
  
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
  
 Na przykład pracy, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Tworzenie kontraktu usługi zgodnego AJAX  
 Domyślnie kontraktów usług uwidaczniany za pośrednictwem danych zwrotnych punktu końcowego AJAX w formacie XML. Domyślnie operacje usług są także dostępne za pośrednictwem żądania HTTP POST do adresów URL, które obejmują adres punktu końcowego, a następnie według nazwy operacji, jak pokazano w poniższym przykładzie.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Ta operacja jest dostępna przy użyciu protokołu HTTP POST do `http://serviceaddress/endpointaddress/GetCities` i zwraca komunikat XML.  
  
 Pełny Model programowania sieci Web umożliwia dostosowanie tych podstawowych właściwości. Na przykład można użyć <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty do kontrolowania zlecenie HTTP, na które odpowiada operacji lub użyj `UriTemplate` właściwości tych odpowiednich atrybutów, aby określić identyfikatory URI niestandardowych. Aby uzyskać więcej informacji, zobacz [modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tematu.  
  
 Format danych JSON jest często używane w usługach interfejsu AJAX. Aby utworzyć operację zwracającą JSON zamiast XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) dla właściwości <xref:System.ServiceModel.Web.WebMessageFormat.Json>. [Serializacji JSON autonomicznego](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) temacie przedstawiono sposób wbudowanych .NET danych i typów kontraktu typy mapy do formatu JSON.  
  
 Zwykle JSON żądań i odpowiedzi składa się z tylko jednego elementu. Dla poprzedniego `GetCities` działania, żądania przypomina następującą instrukcję.  
  
```  
"na"  
```  
  
 Poniższa instrukcja jest podobny do odpowiedzi na to żądanie.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Jeśli operacja przyjmuje dodatkowych parametrów, styl żądanie może opakowana opakowywać obydwu tych parametrów w pojedynczy obiekt JSON. Przykładem tego stylu komunikatu JSON jest w poniższym przykładzie.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Następujące kontraktu akceptuje tego komunikatu.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Uzyskiwanie dostępu do usług AJAX  
 Punktów końcowych WCF AJAX zawsze akceptowania żądań JSON i XML.  
  
 Żądania HTTP POST z typem zawartości "application/json" są traktowane jako JSON, a te z typem zawartości XML (na przykład "text/xml") wskazujące, są traktowane jako XML.  
  
 Żądania HTTP GET zawiera wszystkie parametry żądania w adresie URL, do samej siebie.  
  
 Jest użytkownika decyzji o tym, jak utworzyć żądanie HTTP do punktu końcowego. Ponadto użytkownik ma pełną kontrolę nad konstruowania JSON, który wchodzi w skład treści żądania. Przykład tworzenia żądania z kodu JavaScript, zobacz [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
