---
title: "Usługa AJAX z formatami JSON i XML — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d831d4663031419977b75c6cfe183ac4bd52a86
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="37604-102">Usługa AJAX z formatami JSON i XML — przykład</span><span class="sxs-lookup"><span data-stu-id="37604-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="37604-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] można utworzyć usługi asynchronicznego JavaScript i XML (AJAX), która zwraca dane JavaScript Object Notation (JSON) lub XML.</span><span class="sxs-lookup"><span data-stu-id="37604-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="37604-104">Usługa AJAX mogą korzystać za pomocą kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="37604-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="37604-105">Ten przykład jest oparty na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="37604-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="37604-106">W przeciwieństwie do innych próbek AJAX, w tym przykładzie nie korzysta z kodu ASP.NET AJAX i <xref:System.Web.UI.ScriptManager> formantu.</span><span class="sxs-lookup"><span data-stu-id="37604-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="37604-107">W przypadku niektórych konfiguracji dodatkowych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług AJAX są dostępne z dowolnej strony HTML przy użyciu języka JavaScript i pokazane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="37604-107">With some additional configuration, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="37604-108">Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="37604-108">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
 <span data-ttu-id="37604-109">W tym przykładzie pokazano, jak typ odpowiedzi operacji między formatami JSON i XML przełącznika.</span><span class="sxs-lookup"><span data-stu-id="37604-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="37604-110">Ta funkcja jest dostępna, niezależnie od tego, czy usługa jest skonfigurowana można uzyskać dostępu do środowiska ASP.NET AJAX lub stronę klienta HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="37604-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37604-111">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="37604-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="37604-112">Aby umożliwić korzystanie z klientów z systemem innym niż ASP.NET AJAX, użyj <xref:System.ServiceModel.Activation.WebServiceHostFactory> (nie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) w pliku svc.</span><span class="sxs-lookup"><span data-stu-id="37604-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="37604-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory>dodaje <xref:System.ServiceModel.Description.WebHttpEndpoint> standardowy punkt końcowy do usługi.</span><span class="sxs-lookup"><span data-stu-id="37604-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="37604-114">Punkt końcowy jest skonfigurowana na pusty adres względem pliku svc; oznacza to, że adres usługi ma http://localhost/ServiceModelSamples/service.svc z nie dodatkowe sufiksy na inną niż nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="37604-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```html  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="37604-115">Następujących sekcji w pliku Web.config mogą służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="37604-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="37604-116">Można usunąć, jeśli są potrzebne żadne dodatkowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="37604-116">It can be removed if no extra changes are needed.</span></span>  
  
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
  
 <span data-ttu-id="37604-117">Format danych domyślnych <xref:System.ServiceModel.Description.WebHttpEndpoint> jest podczas domyślny format danych XML, <xref:System.ServiceModel.Description.WebScriptEndpoint> jest JSON.</span><span class="sxs-lookup"><span data-stu-id="37604-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="37604-118">Aby uzyskać więcej informacji, zobacz [tworzenie usług AJAX WCF bez platformy ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="37604-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="37604-119">Usługi w poniższym przykładzie jest standardem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z dwóch operacji.</span><span class="sxs-lookup"><span data-stu-id="37604-119">The service in the following sample is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with two operations.</span></span> <span data-ttu-id="37604-120">Zarówno operacje wymagają <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> treści w stylu <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty, które dotyczą `webHttp` zachowania i nie ma żadnego wpływu na przełączniku format danych JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="37604-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 <span data-ttu-id="37604-121">Format odpowiedzi dla operacji jest określony jako XML, co jest ustawieniem domyślnym dla [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="37604-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="37604-122">Jednak dobrze jest jawnie określić format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="37604-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="37604-123">Używa innej operacji `WebInvokeAttribute` atrybutu i jawnie określa JSON zamiast XML dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="37604-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 <span data-ttu-id="37604-124">Należy pamiętać, że w obu przypadkach operacje zwracać typu złożonego `MathResult`, który jest standardem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="37604-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] data contract type.</span></span>  
  
 <span data-ttu-id="37604-125">Klient XmlAjaxClientPage.htm strony sieci Web zawiera kod JavaScript, który wywołuje jednego z poprzednich dwóch operacji, gdy użytkownik kliknie **obliczanie (zwracany JSON)** lub **obliczanie (zwracany XML)**  przyciski na stronie.</span><span class="sxs-lookup"><span data-stu-id="37604-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="37604-126">Kod, aby wywołać usługę konstruuje treść kodu JSON i wysyła je przy użyciu metody POST protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="37604-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="37604-127">Żądanie jest tworzony ręcznie w języku JavaScript, w odróżnieniu od [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki i przykłady, za pomocą kodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="37604-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  
  
```  
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
  
 <span data-ttu-id="37604-128">Gdy usługa odpowiada, odpowiedź zostanie wyświetlona bez dalszego przetwarzania w polu tekstowym na stronie.</span><span class="sxs-lookup"><span data-stu-id="37604-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="37604-129">To jest zaimplementowany dla celów demonstracyjnych, co pozwala na bezpośrednio Sprawdź formaty danych XML i JSON, używane.</span><span class="sxs-lookup"><span data-stu-id="37604-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  
  
```  
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="37604-130">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="37604-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37604-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="37604-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="37604-132">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="37604-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37604-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="37604-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37604-134">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="37604-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="37604-135">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37604-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="37604-136">Skompiluj rozwiązanie XmlAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37604-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="37604-137">Przejdź do http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (nie należy otwierać XmlAjaxClientPage.htm w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="37604-137">Navigate to http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37604-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37604-138">See Also</span></span>  
 [<span data-ttu-id="37604-139">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="37604-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
