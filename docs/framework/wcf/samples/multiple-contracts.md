---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: e942c6d4a20ae3578d946edb39a7a3d4b0ea8f27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523171"
---
# <a name="multiple-contracts"></a><span data-ttu-id="b27fd-102">Wiele kontraktów</span><span class="sxs-lookup"><span data-stu-id="b27fd-102">Multiple Contracts</span></span>
<span data-ttu-id="b27fd-103">Wiele kontraktów w przykładzie pokazano, jak zaimplementować więcej niż jednego kontraktu usługi i sposobie konfigurowania punktów końcowych do komunikowania się z każdym zaimplementowane kontrakty.</span><span class="sxs-lookup"><span data-stu-id="b27fd-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="b27fd-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b27fd-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="b27fd-105">Usługa została zmodyfikowana, aby zdefiniować dwa kontrakty `ICalculator` kontraktu i `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b27fd-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b27fd-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b27fd-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b27fd-107">Klasa usługi implementuje interfejsy `ICalculator` i `ICalculatorSession` umów.</span><span class="sxs-lookup"><span data-stu-id="b27fd-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="b27fd-108">Jedną z umów wymagają sesję, dlatego usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia, aby utrzymywać stan przez cały okres istnienia sesji.</span><span class="sxs-lookup"><span data-stu-id="b27fd-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="b27fd-109">Konfiguracja usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe do udostępnienia każdej umowy.</span><span class="sxs-lookup"><span data-stu-id="b27fd-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="b27fd-110">`ICalculator` Punkt końcowy jest uwidaczniany na adres bazowy przy użyciu `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b27fd-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="b27fd-111">`ICalculatorSession` Punkt końcowy jest uwidaczniany w baseaddress/sesji przy użyciu `wsHttpBinding` z `bindingConfiguration` ustawioną wartość atrybutu `BindingWithSession`, jak pokazano na poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b27fd-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b27fd-112">Wygenerowanego kodu klienta zawiera teraz klasę klienta dla zarówno oryginał `ICalculator` kontraktu i nowym `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b27fd-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="b27fd-113">Konfiguracja klienta i kod zostały zmodyfikowane w celu komunikowania się z każdej umowy w punkcie końcowym odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="b27fd-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="b27fd-114">Klient jest aplikacji konsoli systemu windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="b27fd-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="b27fd-115">Usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="b27fd-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="b27fd-116">W oknie konsoli klienta wyświetlane operacje wysyłane do każdego z punktów końcowych, najpierw podstawowego punktu końcowego, następuje bezpiecznego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b27fd-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b27fd-117">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b27fd-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b27fd-118">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27fd-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b27fd-119">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27fd-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b27fd-120">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27fd-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b27fd-121">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b27fd-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b27fd-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b27fd-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b27fd-123">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b27fd-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b27fd-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b27fd-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a><span data-ttu-id="b27fd-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b27fd-125">See also</span></span>
