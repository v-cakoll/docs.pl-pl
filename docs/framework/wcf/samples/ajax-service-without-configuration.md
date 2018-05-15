---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="b3906-102">Usługa AJAX bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b3906-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="b3906-103">W tym przykładzie pokazano, jak używać usługi Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługi, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web) bez użycia żadnej konfiguracji Ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b3906-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="b3906-104">Usługa używa składni specjalne w pliku svc można automatycznie włączyć punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="b3906-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="b3906-105">Obsługa interfejsu AJAX w programie WCF jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu.</span><span class="sxs-lookup"><span data-stu-id="b3906-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="b3906-106">Na przykład przy użyciu programu WCF z ASP.NET AJAX, zobacz [przykłady Ajax](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="b3906-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3906-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3906-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b3906-108">W tym przykładzie bazując na AJAX Service przy użyciu protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b3906-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="b3906-109">Zgodnie z opisem w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> służy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="b3906-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="b3906-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi.</span><span class="sxs-lookup"><span data-stu-id="b3906-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="b3906-111">Jeśli żadne zmiany konfiguracji trzeba wprowadzić do punktu końcowego `<system.ServiceModel>` sekcji można całkowicie usunięte z pliku Web.config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="b3906-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="b3906-112">Plik Web.config zawiera niektórych ustawień platformy ASP.NET, które są używane przez ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="b3906-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="b3906-113">Jeśli, które nie były wielkość liter, można usunąć cały plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="b3906-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3906-114">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b3906-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b3906-115">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b3906-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3906-116">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b3906-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3906-117">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b3906-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3906-118">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b3906-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b3906-119">Upewnij się, że wykonać instrukcje dotyczące instalacji w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3906-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b3906-120">Skompiluj rozwiązanie ConfigFreeAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3906-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b3906-121">Przejdź do http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (nie należy otwierać ConfigFreeClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="b3906-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3906-122">Podczas uruchamiania tego przykładu, upewnij się, że uwierzytelniania anonimowego i uwierzytelniania systemu Windows nie są włączone jednocześnie folderu ServiceModelSamples w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="b3906-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="b3906-123">Jeśli tak jest, Wyłącz uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b3906-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="b3906-124">Po uruchomieniu próbki włączyć uwierzytelnianie systemu Windows i uruchom "polecenie iisreset".</span><span class="sxs-lookup"><span data-stu-id="b3906-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3906-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3906-125">See Also</span></span>  
 [<span data-ttu-id="b3906-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="b3906-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
