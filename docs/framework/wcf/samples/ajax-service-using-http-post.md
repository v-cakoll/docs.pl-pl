---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c102d9d403cefb1bf3d4ab75859a81172895c2e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659543"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="b7f79-102">Usługa AJAX używająca żądań POST protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="b7f79-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="b7f79-103">W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronicznego języka JavaScript i XML (technologia AJAX) usługą, która używa metody POST protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b7f79-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="b7f79-104">Usługa AJAX to taki, który możesz uzyskać dostęp przy użyciu podstawowego kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b7f79-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="b7f79-105">W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) Przykładowe; Jedyną różnicą między dwa przykłady jest użycie metody POST protokołu HTTP zamiast HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="b7f79-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="b7f79-106">Obsługa technologii AJAX w Windows Communication Foundation (WCF) została zoptymalizowana do użytku przy użyciu rozszerzeń ASP.NET AJAX za pośrednictwem `ScriptManager` kontroli.</span><span class="sxs-lookup"><span data-stu-id="b7f79-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="b7f79-107">Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="b7f79-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f79-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b7f79-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b7f79-109">Usługa w poniższym przykładzie jest usługi WCF nie kodu specyficznego dla technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="b7f79-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="b7f79-110">Jeśli <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut jest stosowany w przypadku operacji lub <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, czasownik HTTP domyślnej ("POST") jest używany.</span><span class="sxs-lookup"><span data-stu-id="b7f79-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="b7f79-111">Żądania POST jest trudniejsze do konstruowania niż żądania GET, ale nie są buforowane; Użyj żądania POST dla wszystkich operacji, w których pamięci podręcznej nie jest odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="b7f79-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="b7f79-112">Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>— podobnie jak w przykładzie podstawowa usługa AJAX.</span><span class="sxs-lookup"><span data-stu-id="b7f79-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="b7f79-113">Inaczej niż w przypadku żądania GET nie można wywołać usługi WPIS w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="b7f79-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="b7f79-114">Na przykład, przechodząc do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 powoduje błąd, ponieważ usługa WPIS oczekuje `n1` i `n2` parametrów do wysłania w treści wiadomości — w formacie JSON — a nie w adresie URL.</span><span class="sxs-lookup"><span data-stu-id="b7f79-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="b7f79-115">Klient PostAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET, aby wywołać usługę, gdy użytkownik kliknie jeden z przycisków operacji na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="b7f79-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="b7f79-116">Usługa odpowiada w taki sam sposób jak w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki, przy użyciu żądania GET.</span><span class="sxs-lookup"><span data-stu-id="b7f79-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7f79-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b7f79-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b7f79-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b7f79-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7f79-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b7f79-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7f79-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b7f79-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7f79-121">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b7f79-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b7f79-122">Upewnij się, że wykonano instrukcje dotyczące konfigurowania [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7f79-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b7f79-123">Skompiluj rozwiązanie PostAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7f79-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b7f79-124">Przejdź do http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (nie należy otwierać PostAjaxClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="b7f79-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f79-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7f79-125">See Also</span></span>
