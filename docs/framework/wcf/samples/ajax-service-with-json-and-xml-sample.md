---
title: Usługa AJAX z formatami JSON i XML — przykład
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: eadb884667a0b29ef36056f0c3bec4675b7f1b05
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895138"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Usługa AJAX z formatami JSON i XML — przykład

Ten przykład pokazuje, jak używać Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi JavaScript i XML (AJAX), która zwraca dane JavaScript Object Notation (JSON) lub XML. Dostęp do usługi AJAX można uzyskać za pomocą kodu JavaScript z klienta przeglądarki sieci Web. Ten przykład kompiluje się na [podstawowym przykładzie usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .

W przeciwieństwie do innych przykładów AJAX, ten przykład nie używa ASP.NET AJAX i <xref:System.Web.UI.ScriptManager> kontrolki. W przypadku dodatkowej konfiguracji usługi WCF AJAX są dostępne z dowolnej strony HTML za pośrednictwem języka JavaScript, a ten scenariusz jest przedstawiony tutaj. Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [AJAX Samples](ajax.md).

Ten przykład pokazuje, jak przełączyć typ odpowiedzi operacji między JSON i XML. Ta funkcja jest dostępna niezależnie od tego, czy dostęp do usługi jest skonfigurowany za pomocą ASP.NET AJAX, czy na stronie klienta HTML/JavaScript.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Aby umożliwić korzystanie z klientów non-ASP.NET AJAX, użyj <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku SVC. <xref:System.ServiceModel.Activation.WebServiceHostFactory><xref:System.ServiceModel.Description.WebHttpEndpoint> dodaje standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowany z pustym adresem względem pliku SVC; oznacza to, że adres usługi to `http://localhost/ServiceModelSamples/service.svc`, bez dodatkowych sufiksów innych niż nazwa operacji.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

Poniższa sekcja w pliku Web. config może służyć do wprowadzania dodatkowych zmian w konfiguracji punktu końcowego. Można je usunąć, jeśli nie są potrzebne żadne dodatkowe zmiany.

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

Domyślny format danych dla <xref:System.ServiceModel.Description.WebHttpEndpoint> jest XML, podczas gdy domyślny format danych dla <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON. Aby uzyskać więcej informacji, zobacz [Tworzenie usług WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).

Usługa w poniższym przykładzie jest standardową usługą WCF z dwiema operacjami. Obie operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> stylu treści <xref:System.ServiceModel.Web.WebGetAttribute> dla lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów, które są specyficzne dla `webHttp` zachowania i nie mają wpływu na przełącznik formatu danych JSON/XML.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

Format odpowiedzi dla operacji jest określony jako XML, co jest ustawieniem domyślnym dla [ \<zachowania > Webhttp](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) . Jednak dobrym sposobem jest jawne określenie formatu odpowiedzi.

Inna operacja używa `WebInvokeAttribute` atrybutu i jawnie określa kod JSON zamiast XML dla odpowiedzi.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Należy zauważyć, że w obu przypadkach operacje zwracają typ złożony, `MathResult`który jest standardowym typem kontraktu danych WCF.

Strona sieci Web klienta XmlAjaxClientPage. htm zawiera kod JavaScript, który wywołuje jedną z poprzednich dwóch operacji, gdy użytkownik kliknie przyciski **wykonaj obliczenia (Return JSON)** lub **Wykonaj obliczenie (zwrotny kod XML)** na stronie. Kod do wywołania usługi konstruuje treść JSON i wysyła go przy użyciu protokołu HTTP POST. Żądanie jest tworzone ręcznie w języku JavaScript, w przeciwieństwie do przykładowej [podstawowej usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , a inne przykłady przy użyciu ASP.NET AJAX.

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

Gdy usługa reaguje, odpowiedź jest wyświetlana bez dalszych operacji przetwarzania w polu tekstowym na stronie. Ta implementacja jest zaimplementowana w celach demonstracyjnych, aby umożliwić bezpośrednio przestrzeganie używanych formatów danych XML i JSON.

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Skompiluj rozwiązanie XmlAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Przejdź do `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (nie otwieraj XmlAjaxClientPage. htm w przeglądarce z katalogu projektu).

## <a name="see-also"></a>Zobacz także

- [Usługa AJAX używająca żądań POST protokołu HTTP](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
