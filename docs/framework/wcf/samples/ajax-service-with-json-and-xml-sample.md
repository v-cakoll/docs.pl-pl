---
title: Usługa AJAX z formatami JSON i XML — przykład
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: ca9bdbfa135ac7dc0b69589d4f8fce07bc4c4afe
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716215"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="cf075-102">Usługa AJAX z formatami JSON i XML — przykład</span><span class="sxs-lookup"><span data-stu-id="cf075-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="cf075-103">Ten przykład pokazuje, jak używać Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi JavaScript i XML (AJAX), która zwraca dane JavaScript Object Notation (JSON) lub XML.</span><span class="sxs-lookup"><span data-stu-id="cf075-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="cf075-104">Dostęp do usługi AJAX można uzyskać za pomocą kodu JavaScript z klienta przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cf075-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="cf075-105">Ten przykład kompiluje się na [podstawowym przykładzie usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="cf075-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="cf075-106">W przeciwieństwie do innych przykładów AJAX, ten przykład nie używa ASP.NET AJAX i kontrolki <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="cf075-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="cf075-107">W przypadku dodatkowej konfiguracji usługi WCF AJAX są dostępne z dowolnej strony HTML za pośrednictwem języka JavaScript, a ten scenariusz jest przedstawiony tutaj.</span><span class="sxs-lookup"><span data-stu-id="cf075-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="cf075-108">Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [AJAX Samples](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="cf075-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="cf075-109">Ten przykład pokazuje, jak przełączyć typ odpowiedzi operacji między JSON i XML.</span><span class="sxs-lookup"><span data-stu-id="cf075-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="cf075-110">Ta funkcja jest dostępna niezależnie od tego, czy dostęp do usługi jest skonfigurowany za pomocą ASP.NET AJAX, czy na stronie klienta HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="cf075-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="cf075-111">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cf075-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="cf075-112">Aby umożliwić korzystanie z klientów non-ASP.NET AJAX, należy użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="cf075-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="cf075-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> dodaje do usługi <xref:System.ServiceModel.Description.WebHttpEndpoint> standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="cf075-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="cf075-114">Punkt końcowy jest skonfigurowany z pustym adresem względem pliku SVC; oznacza to, że adres usługi jest `http://localhost/ServiceModelSamples/service.svc`, bez dodatkowych sufiksów innych niż nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="cf075-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="cf075-115">Poniższa sekcja w pliku Web. config może służyć do wprowadzania dodatkowych zmian w konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cf075-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="cf075-116">Można je usunąć, jeśli nie są potrzebne żadne dodatkowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="cf075-116">It can be removed if no extra changes are needed.</span></span>

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

<span data-ttu-id="cf075-117">Domyślny format danych <xref:System.ServiceModel.Description.WebHttpEndpoint> jest XML, podczas gdy domyślny format danych dla <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON.</span><span class="sxs-lookup"><span data-stu-id="cf075-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="cf075-118">Aby uzyskać więcej informacji, zobacz [Tworzenie usług WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="cf075-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="cf075-119">Usługa w poniższym przykładzie jest standardową usługą WCF z dwiema operacjami.</span><span class="sxs-lookup"><span data-stu-id="cf075-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="cf075-120">Obie operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> stylu treści na atrybuty <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute>, które są specyficzne dla zachowania `webHttp` i nie mają wpływu na przełącznik formatu danych JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="cf075-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="cf075-121">Format odpowiedzi dla operacji jest określony jako XML, który jest domyślnym ustawieniem zachowania [\<Webhttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="cf075-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="cf075-122">Jednak dobrym sposobem jest jawne określenie formatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cf075-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="cf075-123">Druga operacja używa atrybutu `WebInvokeAttribute` i jawnie określa kod JSON zamiast XML dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cf075-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="cf075-124">Należy zauważyć, że w obu przypadkach operacje zwracają typ złożony, `MathResult`, który jest standardowym typem kontraktu danych WCF.</span><span class="sxs-lookup"><span data-stu-id="cf075-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="cf075-125">Strona sieci Web klienta XmlAjaxClientPage. htm zawiera kod JavaScript, który wywołuje jedną z poprzednich dwóch operacji, gdy użytkownik kliknie przyciski **wykonaj obliczenia (Return JSON)** lub **Wykonaj obliczenie (zwrotny kod XML)** na stronie.</span><span class="sxs-lookup"><span data-stu-id="cf075-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="cf075-126">Kod do wywołania usługi konstruuje treść JSON i wysyła go przy użyciu protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="cf075-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="cf075-127">Żądanie jest tworzone ręcznie w języku JavaScript, w przeciwieństwie do przykładowej [podstawowej usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , a inne przykłady przy użyciu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="cf075-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

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

<span data-ttu-id="cf075-128">Gdy usługa reaguje, odpowiedź jest wyświetlana bez dalszych operacji przetwarzania w polu tekstowym na stronie.</span><span class="sxs-lookup"><span data-stu-id="cf075-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="cf075-129">Ta implementacja jest zaimplementowana w celach demonstracyjnych, aby umożliwić bezpośrednio przestrzeganie używanych formatów danych XML i JSON.</span><span class="sxs-lookup"><span data-stu-id="cf075-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="cf075-130">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cf075-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf075-131">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="cf075-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cf075-132">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf075-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf075-133">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf075-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf075-134">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="cf075-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cf075-135">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf075-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="cf075-136">Skompiluj rozwiązanie XmlAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf075-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="cf075-137">Przejdź do `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (nie należy otwierać XmlAjaxClientPage. htm w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="cf075-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf075-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf075-138">See also</span></span>

- [<span data-ttu-id="cf075-139">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="cf075-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
