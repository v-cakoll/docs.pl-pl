---
title: "Usługa AJAX bez konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf0ed4e1c06bc464b8ebeffbf3be10de3064f479
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="441e7-102">Usługa AJAX bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="441e7-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="441e7-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utworzyć podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługi, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web) bez użycia wszystkich ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="441e7-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="441e7-104">Usługa używa składni specjalne w pliku svc można automatycznie włączyć punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="441e7-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="441e7-105">Obsługa interfejsu AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu.</span><span class="sxs-lookup"><span data-stu-id="441e7-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="441e7-106">Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady Ajax](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="441e7-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="441e7-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="441e7-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="441e7-108">W tym przykładzie bazując na AJAX Service przy użyciu protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="441e7-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="441e7-109">Zgodnie z opisem w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> służy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="441e7-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="441e7-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi.</span><span class="sxs-lookup"><span data-stu-id="441e7-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="441e7-111">Jeśli żadne zmiany konfiguracji trzeba wprowadzić do punktu końcowego \<systemu. ServiceModel > sekcji można całkowicie usunięte z pliku Web.config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="441e7-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="441e7-112">Plik Web.config zawiera niektórych ustawień platformy ASP.NET, które są używane przez ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="441e7-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="441e7-113">Jeśli, które nie były wielkość liter, można usunąć cały plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="441e7-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="441e7-114">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="441e7-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="441e7-115">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="441e7-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="441e7-116">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="441e7-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="441e7-117">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="441e7-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="441e7-118">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="441e7-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="441e7-119">Upewnij się, że wykonać instrukcje dotyczące instalacji w [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="441e7-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="441e7-120">Skompiluj rozwiązanie ConfigFreeAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="441e7-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="441e7-121">Przejdź do http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (nie należy otwierać ConfigFreeClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="441e7-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="441e7-122">Podczas uruchamiania tego przykładu, upewnij się, że uwierzytelniania anonimowego i uwierzytelniania systemu Windows nie są włączone jednocześnie folderu ServiceModelSamples w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="441e7-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="441e7-123">Jeśli tak jest, Wyłącz uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="441e7-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="441e7-124">Po uruchomieniu próbki włączyć uwierzytelnianie systemu Windows i uruchom "polecenie iisreset".</span><span class="sxs-lookup"><span data-stu-id="441e7-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441e7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="441e7-125">See Also</span></span>  
 [<span data-ttu-id="441e7-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="441e7-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
