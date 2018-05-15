---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 8e96d1ac27eb69d8e7e4da76aa8679aa35bf8ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="multiple-contracts"></a><span data-ttu-id="7c53c-102">Wiele kontraktów</span><span class="sxs-lookup"><span data-stu-id="7c53c-102">Multiple Contracts</span></span>
<span data-ttu-id="7c53c-103">Przykład wielu umów przedstawiono sposoby zaimplementować więcej niż jeden kontrakt na usługę oraz sposobu konfigurowania punktów końcowych do komunikowania się z każdym zaimplementowanych kontraktów.</span><span class="sxs-lookup"><span data-stu-id="7c53c-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="7c53c-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7c53c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="7c53c-105">Usługa została zmodyfikowana, aby zdefiniować dwa kontrakty `ICalculator` kontraktu i `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7c53c-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c53c-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7c53c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7c53c-107">Klasa usługi implementuje zarówno `ICalculator` i `ICalculatorSession` umów.</span><span class="sxs-lookup"><span data-stu-id="7c53c-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="7c53c-108">Wymaga jednego umów sesji, dlatego usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia, aby zachować stan okresu istnienia sesji.</span><span class="sxs-lookup"><span data-stu-id="7c53c-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="7c53c-109">Konfiguracja usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe do udostępnienia każdej umowy.</span><span class="sxs-lookup"><span data-stu-id="7c53c-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="7c53c-110">`ICalculator` Punktu końcowego jest uwidaczniany za pomocą adresu podstawowego `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7c53c-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="7c53c-111">`ICalculatorSession` Punktu końcowego jest uwidaczniany za pomocą baseaddress/sesji `wsHttpBinding` z `bindingConfiguration` ustawić atrybutu `BindingWithSession`, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7c53c-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="7c53c-112">Kod wygenerowanego klienta zawiera teraz klasę klienta dla obu oryginalnej `ICalculator` kontraktu i nowych `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7c53c-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="7c53c-113">Konfiguracja klienta i kod został zmodyfikowany w celu komunikowania się z każdej umowy w punkcie końcowym odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="7c53c-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="7c53c-114">Klient jest aplikacji konsoli systemu windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="7c53c-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="7c53c-115">Usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="7c53c-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="7c53c-116">Okno konsoli klienta Wyświetla operacje wysyłane do każdego z punktów końcowych, najpierw podstawowy punkt końcowy, następuje bezpiecznego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7c53c-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c53c-117">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7c53c-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7c53c-118">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7c53c-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7c53c-119">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7c53c-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7c53c-120">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7c53c-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c53c-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7c53c-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c53c-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7c53c-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c53c-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7c53c-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c53c-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7c53c-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a><span data-ttu-id="7c53c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c53c-125">See Also</span></span>
