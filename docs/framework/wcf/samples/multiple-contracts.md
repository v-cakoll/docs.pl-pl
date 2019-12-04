---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: d8e86682e18d0319476d33c16d3caa5a4337f983
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714744"
---
# <a name="multiple-contracts"></a><span data-ttu-id="c773a-102">Wiele kontraktów</span><span class="sxs-lookup"><span data-stu-id="c773a-102">Multiple Contracts</span></span>
<span data-ttu-id="c773a-103">Przykład wielu kontraktów pokazuje, jak zaimplementować więcej niż jeden kontrakt w usłudze i jak skonfigurować punkty końcowe do komunikowania się z każdą z zaimplementowanych kontraktów.</span><span class="sxs-lookup"><span data-stu-id="c773a-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="c773a-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c773a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c773a-105">Usługa została zmodyfikowana w celu zdefiniowania dwóch kontraktów, kontraktu `ICalculator` i kontraktu `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="c773a-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c773a-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c773a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c773a-107">Klasa usługi implementuje zarówno kontrakt `ICalculator`, jak i `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="c773a-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="c773a-108">Ponieważ jeden z kontraktów wymaga sesji, usługa używa trybu wystąpienia <xref:System.ServiceModel.InstanceContextMode.PerSession>, aby zachować stan w okresie istnienia sesji.</span><span class="sxs-lookup"><span data-stu-id="c773a-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="c773a-109">Konfiguracja usługi została zmodyfikowana w celu zdefiniowania dwóch punktów końcowych, aby uwidocznić każdy kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c773a-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="c773a-110">Punkt końcowy `ICalculator` jest uwidoczniony pod adresem podstawowym przy użyciu `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="c773a-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="c773a-111">Punkt końcowy `ICalculatorSession` jest udostępniany w BaseAddress/sesji przy użyciu `wsHttpBinding` z atrybutem `bindingConfiguration` ustawionym na `BindingWithSession`, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="c773a-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="c773a-112">Wygenerowany kod klienta zawiera teraz klasę klienta zarówno dla oryginalnego kontraktu `ICalculator`, jak i nowego kontraktu `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="c773a-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="c773a-113">Konfiguracja i kod klienta zostały zmodyfikowane w celu komunikowania się z każdą umową w odpowiednim punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="c773a-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="c773a-114">Klient jest aplikacją dla systemu Windows (exe).</span><span class="sxs-lookup"><span data-stu-id="c773a-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="c773a-115">Usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c773a-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="c773a-116">W oknie konsoli klienta są wyświetlane operacje wysyłane do poszczególnych punktów końcowych, pierwszy punkt końcowy podstawowego, a następnie bezpieczny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="c773a-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c773a-117">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="c773a-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c773a-118">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c773a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c773a-119">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c773a-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c773a-120">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c773a-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c773a-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c773a-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c773a-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c773a-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c773a-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c773a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c773a-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c773a-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
