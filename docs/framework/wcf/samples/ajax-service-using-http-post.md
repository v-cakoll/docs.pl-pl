---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1446fadeb249d91f0eb3e65b1155f00090441a5a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="cbc6a-102">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="cbc6a-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="cbc6a-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utworzyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronicznego JavaScript i XML (AJAX) usługa, która używa metody POST protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="cbc6a-104">Usługa AJAX to takie, które są dostępne przy użyciu podstawowego kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="cbc6a-105">Ten przykład jest oparty na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) przykładowa; jedyną różnicą między dwoma próbki jest użycie metody POST protokołu HTTP zamiast HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="cbc6a-106">Obsługa interfejsu AJAX w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-106">AJAX support in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="cbc6a-107">Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="cbc6a-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbc6a-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cbc6a-109">Usługi w poniższym przykładzie jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z żadnego kodu specyficzne dla interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="cbc6a-110">Jeśli <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut jest stosowany w przypadku operacji lub <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, jest używany domyślny zlecenie HTTP ("POST").</span><span class="sxs-lookup"><span data-stu-id="cbc6a-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="cbc6a-111">Żądania POST jest utrudnione do skonstruowania niż żądania GET, ale nie są buforowane; Użyj żądania POST dla wszystkich operacji, gdy buforowanie nie jest odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="cbc6a-112">Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, po prostu tak jak na przykład podstawowa usługa AJAX.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="cbc6a-113">W przeciwieństwie do żądania GET nie można wywołać usługi POST z przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="cbc6a-114">Na przykład, przechodząc do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 zakończy się błędem, ponieważ usługa POST oczekuje `n1` i `n2` parametrów do wysłania w treści wiadomości — w formacie JSON —, a nie w adresie URL.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="cbc6a-115">Klient PostAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET można wywołać usługi, gdy użytkownik kliknie jeden z przycisków operacji na stronie.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="cbc6a-116">Usługa odpowiada w taki sam sposób jak w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki z żądania GET.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbc6a-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cbc6a-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cbc6a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cbc6a-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cbc6a-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cbc6a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cbc6a-121">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="cbc6a-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cbc6a-122">Upewnij się, że wykonać instrukcje dotyczące instalacji [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbc6a-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cbc6a-123">Skompiluj rozwiązanie PostAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cbc6a-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cbc6a-124">Przejdź do http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (nie należy otwierać PostAjaxClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="cbc6a-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc6a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbc6a-125">See Also</span></span>
