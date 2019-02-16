---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 2ea5c61ea3f0f8adcce6dc14be11a8b098c7ca0f
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332926"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="bea99-102">Usługa AJAX bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bea99-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="bea99-103">W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznych w języku JavaScript i XML (technologia AJAX) (usługa, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web), bez używania konfiguracji Ustawienia.</span><span class="sxs-lookup"><span data-stu-id="bea99-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="bea99-104">Usługa używa specjalnej składni w pliku SVC, można automatycznie włączyć punkt końcowy interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="bea99-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="bea99-105">Obsługa technologii AJAX w programie WCF jest zoptymalizowany do użytku z programem ASP.NET AJAX za pośrednictwem `ScriptManager` kontroli.</span><span class="sxs-lookup"><span data-stu-id="bea99-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="bea99-106">Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="bea99-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bea99-107">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="bea99-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bea99-108">Ten przykład tworzy po AJAX Service przy użyciu protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="bea99-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="bea99-109">Zgodnie z opisem w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) przykładzie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> służy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="bea99-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="bea99-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi.</span><span class="sxs-lookup"><span data-stu-id="bea99-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="bea99-111">Jeśli żadne zmiany konfiguracji potrzebne do endpoint, `<system.ServiceModel>` sekcji można całkowicie usunięte z pliku Web.config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="bea99-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="bea99-112">Plik Web.config zawiera kilka ustawień platformy ASP.NET, które są używane przez ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="bea99-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="bea99-113">Jeśli uprzednio nie tak, udało się usunąć cały plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="bea99-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bea99-114">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bea99-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bea99-115">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bea99-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bea99-116">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="bea99-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bea99-117">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bea99-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bea99-118">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="bea99-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bea99-119">Upewnij się, że wykonać instrukcje instalacji [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea99-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bea99-120">Skompiluj rozwiązanie ConfigFreeAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bea99-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bea99-121">Przejdź do `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (nie należy otwierać ConfigFreeClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="bea99-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bea99-122">Podczas uruchamiania tego przykładu, upewnij się, że uwierzytelnianie anonimowe i uwierzytelnianie Windows nie są włączone jednocześnie dla folderu ServiceModelSamples w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="bea99-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="bea99-123">Jeśli tak jest rzeczywiście, Wyłącz uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="bea99-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="bea99-124">Po uruchomieniu przykładu, włączyć uwierzytelnianie Windows, a następnie uruchom "polecenie iisreset".</span><span class="sxs-lookup"><span data-stu-id="bea99-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea99-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bea99-125">See also</span></span>
- [<span data-ttu-id="bea99-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="bea99-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
