---
title: Usługa AJAX z formatami JSON i XML — przykład
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e5f2838575b212f6b95fd01b469d771017ef534c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207490"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="6a949-102">Usługa AJAX z formatami JSON i XML — przykład</span><span class="sxs-lookup"><span data-stu-id="6a949-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="6a949-103">W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia asynchronicznych języka JavaScript i XML (technologia AJAX) usługa, która zwraca dane JavaScript Object Notation (JSON) lub XML.</span><span class="sxs-lookup"><span data-stu-id="6a949-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="6a949-104">Usługa AJAX dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a949-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="6a949-105">W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="6a949-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="6a949-106">W przeciwieństwie do innych przykładów AJAX, w tym przykładzie nie korzysta z technologii ASP.NET AJAX i <xref:System.Web.UI.ScriptManager> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6a949-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="6a949-107">Za pomocą dodatkowej konfiguracji usług WCF AJAX jest możliwy z dowolnej strony HTML przy użyciu języka JavaScript, a w tym scenariuszu jest następująca.</span><span class="sxs-lookup"><span data-stu-id="6a949-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="6a949-108">Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="6a949-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>
  
 <span data-ttu-id="6a949-109">Niniejszy przykład pokazuje, jak przełączyć typ odpowiedzi operacji między formatami JSON i XML.</span><span class="sxs-lookup"><span data-stu-id="6a949-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="6a949-110">Ta funkcja jest dostępna niezależnie od tego, czy usługa jest skonfigurowana do można uzyskać dostępu do kodu ASP.NET AJAX lub strony klienta HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6a949-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a949-111">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6a949-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>
  
<span data-ttu-id="6a949-112">Aby umożliwić korzystanie z klientów — ASP.NET AJAX, należy użyć <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku svc.</span><span class="sxs-lookup"><span data-stu-id="6a949-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <xref:System.ServiceModel.Activation.WebServiceHostFactory> <span data-ttu-id="6a949-113">dodaje <xref:System.ServiceModel.Description.WebHttpEndpoint> standardowy punkt końcowy do usługi.</span><span class="sxs-lookup"><span data-stu-id="6a949-113">adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="6a949-114">Punkt końcowy jest skonfigurowana pod adresem pusty względem plików .svc; oznacza, że adres usługi `http://localhost/ServiceModelSamples/service.svc`, za pomocą nie dodatkowe sufiksy inna niż nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="6a949-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="6a949-115">Poniższej sekcji w pliku Web.config może służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6a949-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="6a949-116">Można je usunąć, jeśli są wymagane żadne dodatkowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="6a949-116">It can be removed if no extra changes are needed.</span></span>  
  
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
  
 <span data-ttu-id="6a949-117">Domyślne dane formatu dla <xref:System.ServiceModel.Description.WebHttpEndpoint> podczas domyślny format danych jest XML, <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON.</span><span class="sxs-lookup"><span data-stu-id="6a949-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="6a949-118">Aby uzyskać więcej informacji, zobacz [tworzenie usług AJAX WCF bez platformy ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="6a949-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="6a949-119">Usługa w poniższym przykładzie jest standardowa usługi WCF, za pomocą dwie operacje.</span><span class="sxs-lookup"><span data-stu-id="6a949-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="6a949-120">Obie operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style na <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty, które są specyficzne dla `webHttp` zachowania i nie ma żadnego wpływu na przełączniku format danych JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="6a949-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="6a949-121">Format odpowiedzi dla operacji jest określony jako XML, co jest ustawieniem domyślnym dla [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6a949-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="6a949-122">Jednak dobrą praktyką jest jawnie określić format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6a949-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="6a949-123">Używa innej operacji `WebInvokeAttribute` atrybutu i jawnie określa JSON zamiast XML dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6a949-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="6a949-124">Należy pamiętać, że w obu przypadkach operacji zwraca typ złożony, `MathResult`, czyli standardowego typu kontraktu danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="6a949-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>  
  
 <span data-ttu-id="6a949-125">Klient XmlAjaxClientPage.htm strony sieci Web zawiera kod JavaScript, która wywołuje jedną z dwóch poprzednich operacji, gdy użytkownik kliknie **wykonywanie obliczeń (zwracany kod JSON)** lub **wykonywanie obliczeń (zwracany XML)**  przyciski na stronie.</span><span class="sxs-lookup"><span data-stu-id="6a949-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="6a949-126">Kod, aby wywołać usługę tworzy treść kodu JSON i wysyła je za pomocą żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="6a949-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="6a949-127">Żądanie jest tworzony ręcznie w języku JavaScript, w odróżnieniu od [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki i przykłady, za pomocą kodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="6a949-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

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

 <span data-ttu-id="6a949-128">Gdy usługa odpowiada, odpowiedź zostanie wyświetlona bez dalszego przetwarzania w polu tekstowym na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="6a949-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="6a949-129">To jest zaimplementowane w celach demonstracyjnych możliwe było bezpośrednio obserwować formatów danych XML i JSON używanych.</span><span class="sxs-lookup"><span data-stu-id="6a949-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="6a949-130">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6a949-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a949-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6a949-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6a949-132">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="6a949-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a949-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6a949-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6a949-134">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="6a949-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6a949-135">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6a949-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6a949-136">Skompiluj rozwiązanie XmlAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6a949-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6a949-137">Przejdź do `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (nie należy otwierać XmlAjaxClientPage.htm w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="6a949-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a949-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a949-138">See also</span></span>

- [<span data-ttu-id="6a949-139">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="6a949-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
