---
title: Usługa AJAX z formatami JSON i XML — przykład
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 1beb89c11fccefec24ccbebc3fe30033a646718d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452693"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Usługa AJAX z formatami JSON i XML — przykład
W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia asynchronicznych języka JavaScript i XML (technologia AJAX) usługa, która zwraca dane JavaScript Object Notation (JSON) lub XML. Usługa AJAX dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web. W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.  
  
 W przeciwieństwie do innych przykładów AJAX, w tym przykładzie nie korzysta z technologii ASP.NET AJAX i <xref:System.Web.UI.ScriptManager> kontroli. Za pomocą dodatkowej konfiguracji usług WCF AJAX jest możliwy z dowolnej strony HTML przy użyciu języka JavaScript, a w tym scenariuszu jest następująca. Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Niniejszy przykład pokazuje, jak przełączyć typ odpowiedzi operacji między formatami JSON i XML. Ta funkcja jest dostępna niezależnie od tego, czy usługa jest skonfigurowana do można uzyskać dostępu do kodu ASP.NET AJAX lub strony klienta HTML/JavaScript.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Aby umożliwić korzystanie z klientów — ASP.NET AJAX, należy użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> dodaje <xref:System.ServiceModel.Description.WebHttpEndpoint> standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowana pod adresem pusty względem plików .svc; oznacza, że adres usługi http://localhost/ServiceModelSamples/service.svc, za pomocą nie dodatkowe sufiksy inna niż nazwa operacji.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Poniższej sekcji w pliku Web.config może służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego. Można je usunąć, jeśli są wymagane żadne dodatkowe zmiany.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Domyślne dane formatu dla <xref:System.ServiceModel.Description.WebHttpEndpoint> podczas domyślny format danych jest XML, <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON. Aby uzyskać więcej informacji, zobacz [tworzenie usług AJAX WCF bez platformy ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 Usługa w poniższym przykładzie jest standardowa usługi WCF, za pomocą dwie operacje. Obie operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style na <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty, które są specyficzne dla `webHttp` zachowania i nie ma żadnego wpływu na przełączniku format danych JSON/XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 Format odpowiedzi dla operacji jest określony jako XML, co jest ustawieniem domyślnym dla [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie. Jednak dobrą praktyką jest jawnie określić format odpowiedzi.  
  
 Używa innej operacji `WebInvokeAttribute` atrybutu i jawnie określa JSON zamiast XML dla odpowiedzi.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Należy pamiętać, że w obu przypadkach operacji zwraca typ złożony, `MathResult`, czyli standardowego typu kontraktu danych programu WCF.  
  
 Klient XmlAjaxClientPage.htm strony sieci Web zawiera kod JavaScript, która wywołuje jedną z dwóch poprzednich operacji, gdy użytkownik kliknie **wykonywanie obliczeń (zwracany kod JSON)** lub **wykonywanie obliczeń (zwracany XML)**  przyciski na stronie. Kod, aby wywołać usługę tworzy treść kodu JSON i wysyła je za pomocą żądania HTTP POST. Żądanie jest tworzony ręcznie w języku JavaScript, w odróżnieniu od [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki i przykłady, za pomocą kodu ASP.NET AJAX.  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 Gdy usługa odpowiada, odpowiedź zostanie wyświetlona bez dalszego przetwarzania w polu tekstowym na tej stronie. To jest zaimplementowane w celach demonstracyjnych możliwe było bezpośrednio obserwować formatów danych XML i JSON używanych.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie XmlAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (nie należy otwierać XmlAjaxClientPage.htm w przeglądarce z katalogu projektu).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa AJAX używająca żądań POST protokołu HTTP](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
