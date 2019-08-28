---
title: Usługa AJAX bez konfiguracji
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: b3c12801d14c7f6850a985c521c0e3fff92ba8e4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045813"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="35c69-102">Usługa AJAX bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="35c69-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="35c69-103">Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznej języka JavaScript i XML (AJAX) (usługi, do której można uzyskać dostęp za pomocą kodu JavaScript z klienta przeglądarki sieci Web) bez użycia żadnej konfiguracji Ustawienia.</span><span class="sxs-lookup"><span data-stu-id="35c69-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="35c69-104">Usługa używa specjalnej składni w pliku SVC, aby automatycznie włączyć punkt końcowy AJAX.</span><span class="sxs-lookup"><span data-stu-id="35c69-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="35c69-105">Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z `ScriptManager` ASP.NET AJAX przez formant.</span><span class="sxs-lookup"><span data-stu-id="35c69-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="35c69-106">Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="35c69-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="35c69-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35c69-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="35c69-108">Ten przykład kompiluje się w usłudze AJAX przy użyciu protokołu HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="35c69-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="35c69-109">Zgodnie z opisem <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> w [podstawowym przykładzie usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) jest używany do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="35c69-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```svc
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="35c69-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> do usługi.</span><span class="sxs-lookup"><span data-stu-id="35c69-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="35c69-111">Jeśli nie trzeba wprowadzać zmian w konfiguracji punktu końcowego, `<system.ServiceModel>` sekcja może zostać całkowicie usunięta z pliku Web. config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="35c69-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="35c69-112">Plik Web. config zawiera kilka ustawień ASP.NET, które są używane przez ConfigFreeClientPage. aspx.</span><span class="sxs-lookup"><span data-stu-id="35c69-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="35c69-113">Jeśli tak się nie dzieje, można usunąć cały plik Web. config.</span><span class="sxs-lookup"><span data-stu-id="35c69-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35c69-114">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="35c69-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="35c69-115">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="35c69-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="35c69-116">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="35c69-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35c69-117">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="35c69-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="35c69-118">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="35c69-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="35c69-119">Upewnij się, że instrukcje instalacji zostały wykonane w [procedurze jednorazowej konfiguracji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35c69-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="35c69-120">Skompiluj rozwiązanie ConfigFreeAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35c69-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="35c69-121">Przejdź do `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (nie otwieraj ConfigFreeClientPage. aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="35c69-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="35c69-122">Podczas uruchamiania tego przykładu upewnij się, że uwierzytelnianie anonimowe i uwierzytelnianie systemu Windows nie są włączone równocześnie dla folderu ServiceModelSamples w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="35c69-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="35c69-123">W takim przypadku należy wyłączyć uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="35c69-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="35c69-124">Po uruchomieniu przykładu Włącz uwierzytelnianie systemu Windows i uruchom polecenie "iisreset".</span><span class="sxs-lookup"><span data-stu-id="35c69-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="35c69-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35c69-125">See also</span></span>

- [<span data-ttu-id="35c69-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="35c69-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
