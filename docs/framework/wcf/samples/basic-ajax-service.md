---
title: Podstawowa usługa AJAX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50d9054da934a50ea02340481c7592e4756306e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="basic-ajax-service"></a><span data-ttu-id="029ae-102">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="029ae-102">Basic AJAX Service</span></span>
<span data-ttu-id="029ae-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] można utworzyć podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługa dostęp można uzyskać przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web).</span><span class="sxs-lookup"><span data-stu-id="029ae-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="029ae-104">Używane przez usługę <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby upewnić się, że usługa odpowiada na żądania HTTP GET i jest skonfigurowana do używania formatu danych JavaScript Object Notation (JSON) na odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="029ae-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="029ae-105">Obsługa interfejsu AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu.</span><span class="sxs-lookup"><span data-stu-id="029ae-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="029ae-106">Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="029ae-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="029ae-107">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="029ae-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="029ae-108">W poniższym kodzie <xref:System.ServiceModel.Web.WebGetAttribute> atrybut jest stosowany do `Add` operację, aby upewnić się, że usługa odpowiada na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="029ae-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="029ae-109">Kod używa operacji GET dla uproszczenia (można utworzyć żądania HTTP GET z dowolnej przeglądarki sieci Web).</span><span class="sxs-lookup"><span data-stu-id="029ae-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="029ae-110">Aby włączyć buforowanie umożliwia także GET.</span><span class="sxs-lookup"><span data-stu-id="029ae-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="029ae-111">HTTP POST jest wartość domyślna w przypadku braku `WebGetAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="029ae-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="029ae-112">Przykładowy plik .svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, która dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> standardowy punkt końcowy do usługi.</span><span class="sxs-lookup"><span data-stu-id="029ae-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="029ae-113">Punkt końcowy jest skonfigurowana na pusty adres względem pliku svc.</span><span class="sxs-lookup"><span data-stu-id="029ae-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="029ae-114">Oznacza to, że adres usługi http://localhost/ServiceModelSamples/service.svc, z nie dodatkowe sufiksy na inną niż nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="029ae-114">This means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="029ae-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Jest wstępnie skonfigurowana, aby udostępnić usługę ze strony klienta ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="029ae-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="029ae-116">Następujących sekcji w pliku Web.config mogą służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="029ae-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="029ae-117">Można usunąć, jeśli są wymagane nie dodatkowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="029ae-117">It can be removed if no extra changes are required.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="029ae-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Ustawia domyślny format danych usługi do formatu JSON, a nie XML.</span><span class="sxs-lookup"><span data-stu-id="029ae-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="029ae-119">Aby wywołać usługę, przejdź do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po zakończeniu zestaw się i kompilacji kroki opisane w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="029ae-119">To invoke the service, navigate to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="029ae-120">Ta funkcja testowania jest włączona za pomocą żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="029ae-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="029ae-121">Klient SimpleAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET można wywołać usługi, gdy użytkownik kliknie jeden z przycisków operacji na stronie.</span><span class="sxs-lookup"><span data-stu-id="029ae-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="029ae-122">`ScriptManager` Kontrola służy do udostępnić serwer proxy do usługi za pomocą skryptu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="029ae-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="029ae-123">Lokalny serwer proxy zostanie uruchomiony i operacje są wywoływane przy użyciu następującego kodu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="029ae-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="029ae-124">Jeśli wywołanie usługi zakończy się powodzeniem, kod wywołuje `onSuccess` obsługi i wyniku operacji jest wyświetlana w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="029ae-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="029ae-125">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="029ae-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="029ae-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="029ae-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="029ae-127">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="029ae-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="029ae-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="029ae-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="029ae-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="029ae-129">See Also</span></span>
