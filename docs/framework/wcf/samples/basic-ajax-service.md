---
title: Podstawowa usługa AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716124"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="5a76d-102">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="5a76d-102">Basic AJAX Service</span></span>

<span data-ttu-id="5a76d-103">Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznej języka JavaScript i XML (AJAX) (usługi, do której można uzyskać dostęp za pomocą kodu JavaScript z klienta przeglądarki sieci Web).</span><span class="sxs-lookup"><span data-stu-id="5a76d-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="5a76d-104">Usługa używa atrybutu <xref:System.ServiceModel.Web.WebGetAttribute>, aby upewnić się, że usługa odpowiada na żądania HTTP GET i jest skonfigurowana do używania formatu danych JSON (JavaScript Object Notation) dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5a76d-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="5a76d-105">Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez formant `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="5a76d-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="5a76d-106">Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="5a76d-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5a76d-107">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a76d-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5a76d-108">W poniższym kodzie atrybut <xref:System.ServiceModel.Web.WebGetAttribute> jest stosowany do operacji `Add`, aby upewnić się, że usługa odpowiada na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="5a76d-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="5a76d-109">Kod używa elementu GET for prostoty (można utworzyć żądanie HTTP GET z dowolnej przeglądarki sieci Web).</span><span class="sxs-lookup"><span data-stu-id="5a76d-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="5a76d-110">Można również użyć GET, aby włączyć buforowanie.</span><span class="sxs-lookup"><span data-stu-id="5a76d-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="5a76d-111">WPIS HTTP POST jest wartością domyślną w nieobecności atrybutu `WebGetAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5a76d-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="5a76d-112">Plik Sample. svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, co powoduje dodanie standardowego punktu końcowego <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi.</span><span class="sxs-lookup"><span data-stu-id="5a76d-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="5a76d-113">Punkt końcowy jest skonfigurowany z pustym adresem względem pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="5a76d-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="5a76d-114">Oznacza to, że adres usługi jest `http://localhost/ServiceModelSamples/service.svc`, bez dodatkowych sufiksów innych niż nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="5a76d-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="5a76d-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> jest wstępnie skonfigurowana, aby usługa była dostępna ze strony klienta AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5a76d-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="5a76d-116">Poniższa sekcja w pliku Web. config może służyć do wprowadzania dodatkowych zmian w konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5a76d-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="5a76d-117">Jeśli nie są wymagane żadne dodatkowe zmiany, można je usunąć.</span><span class="sxs-lookup"><span data-stu-id="5a76d-117">It can be removed if no extra changes are required.</span></span>

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

<span data-ttu-id="5a76d-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> ustawia domyślny format danych dla usługi na JSON zamiast XML.</span><span class="sxs-lookup"><span data-stu-id="5a76d-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="5a76d-119">Aby wywołać usługę, przejdź do `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po zakończeniu kroków konfiguracji i kompilacji przedstawionych w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a76d-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="5a76d-120">Ta funkcja testowa jest włączana za pomocą żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="5a76d-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="5a76d-121">Strona sieci Web klienta SimpleAjaxClientPage. aspx zawiera kod ASP.NET do wywołania usługi za każdym razem, gdy użytkownik kliknie jeden z przycisków operacji na stronie.</span><span class="sxs-lookup"><span data-stu-id="5a76d-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="5a76d-122">Formant `ScriptManager` służy do udostępniania serwerowi proxy usługi dostępnego za pomocą języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5a76d-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="5a76d-123">Zostanie utworzone wystąpienie lokalnego serwera proxy, a operacje są wywoływane przy użyciu następującego kodu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5a76d-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="5a76d-124">Jeśli wywołanie usługi powiedzie się, kod wywoła procedurę obsługi `onSuccess` a wynik operacji zostanie wyświetlony w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5a76d-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="5a76d-125">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a76d-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a76d-126">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5a76d-126">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5a76d-127">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a76d-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a76d-128">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a76d-128">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
