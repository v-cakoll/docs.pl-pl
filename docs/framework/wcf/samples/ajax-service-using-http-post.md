---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 560739c576965d597010a6885b53c7905aaeb8e7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716191"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="c60ef-102">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="c60ef-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="c60ef-103">Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi ASP.NET w języku JavaScript i XML (AJAX) używającej protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="c60ef-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="c60ef-104">Usługa AJAX jest taka, do której można uzyskać dostęp za pomocą podstawowego kodu JavaScript z klienta przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c60ef-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="c60ef-105">Ten przykład kompiluje na [podstawowej próbce usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ; Jedyną różnicą między tymi dwoma próbkami jest użycie polecenia HTTP POST zamiast HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c60ef-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="c60ef-106">Obsługa technologii AJAX w Windows Communication Foundation (WCF) jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez formant `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="c60ef-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="c60ef-107">Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="c60ef-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c60ef-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c60ef-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="c60ef-109">Usługa w poniższym przykładzie jest usługą WCF bez kodu specyficznego dla technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="c60ef-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="c60ef-110">Jeśli atrybut <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany w operacji lub atrybut <xref:System.ServiceModel.Web.WebGetAttribute> nie jest stosowany, zostanie użyte domyślne zlecenie HTTP ("POST").</span><span class="sxs-lookup"><span data-stu-id="c60ef-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="c60ef-111">Żądania POST są trudniejsze do skonstruowania niż żądania GET, ale nie są buforowane. Użyj żądań POST dla wszystkich operacji, gdzie buforowanie jest nieodpowiednie.</span><span class="sxs-lookup"><span data-stu-id="c60ef-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="c60ef-112">Utwórz punkt końcowy AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, podobnie jak w przypadku przykładowej podstawowej usługi AJAX.</span><span class="sxs-lookup"><span data-stu-id="c60ef-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="c60ef-113">W przeciwieństwie do żądań GET nie można wywoływać usług POST z przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="c60ef-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="c60ef-114">Na przykład przechodzenie do `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` powoduje błąd, ponieważ usługa POST oczekuje, że parametry `n1` i `n2` mają być wysyłane w treści wiadomości w formacie JSON, a nie w adresie URL.</span><span class="sxs-lookup"><span data-stu-id="c60ef-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="c60ef-115">Strona sieci Web klienta PostAjaxClientPage. aspx zawiera kod ASP.NET do wywołania usługi za każdym razem, gdy użytkownik kliknie jeden z przycisków operacji na stronie.</span><span class="sxs-lookup"><span data-stu-id="c60ef-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="c60ef-116">Usługa reaguje w taki sam sposób jak w przypadku podstawowego przykładowej [usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) z żądaniem get.</span><span class="sxs-lookup"><span data-stu-id="c60ef-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c60ef-117">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c60ef-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c60ef-118">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c60ef-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c60ef-119">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c60ef-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c60ef-120">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c60ef-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c60ef-121">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="c60ef-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c60ef-122">Upewnij się, że zostały wykonane instrukcje konfiguracji [jednorazowej procedury konfiguracji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c60ef-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c60ef-123">Skompiluj rozwiązanie PostAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c60ef-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="c60ef-124">Przejdź do `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (nie należy otwierać PostAjaxClientPage. aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="c60ef-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
