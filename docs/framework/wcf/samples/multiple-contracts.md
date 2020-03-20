---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144347"
---
# <a name="multiple-contracts"></a><span data-ttu-id="1b9c2-102">Wiele kontraktów</span><span class="sxs-lookup"><span data-stu-id="1b9c2-102">Multiple Contracts</span></span>
<span data-ttu-id="1b9c2-103">Przykład wielu kontraktów pokazuje, jak zaimplementować więcej niż jedną umowę w usłudze i jak skonfigurować punkty końcowe do komunikowania się z każdym z zaimplementowanych kontraktów.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="1b9c2-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="1b9c2-105">Usługa została zmodyfikowana w celu zdefiniowania dwóch umów, `ICalculator` umowy i `ICalculatorSession` umowy.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b9c2-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1b9c2-107">Klasa usługi implementuje `ICalculator` zarówno `ICalculatorSession` i kontrakty.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="1b9c2-108">Ponieważ jedna z umów wymaga sesji, usługa <xref:System.ServiceModel.InstanceContextMode.PerSession> używa trybu wystąpienia, aby utrzymać stan przez cały okres istnienia sesji.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="1b9c2-109">Konfiguracja usługi została zmodyfikowana w celu zdefiniowania dwóch punktów końcowych, aby udostępnić każdy kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="1b9c2-110">Punkt `ICalculator` końcowy jest narażony na `basicHttpBinding`adres podstawowy przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="1b9c2-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="1b9c2-111">Punkt `ICalculatorSession` końcowy jest narażony na adres podstawowy/sesję `bindingConfiguration` przy użyciu `BindingWithSession` `wsHttpBinding` atrybutu ustawionego na , jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="1b9c2-112">Wygenerowany kod klienta zawiera teraz klasę `ICalculator` klienta dla `ICalculatorSession` oryginalnego kontraktu i nowego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="1b9c2-113">Konfiguracja klienta i kod zostały zmodyfikowane w celu komunikowania się z każdą umową w odpowiednim punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="1b9c2-114">Klient jest aplikacją konsoli systemu Windows (.exe).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="1b9c2-115">Usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="1b9c2-116">Okno konsoli klienta wyświetla operacje wysyłane do każdego z punktów końcowych, najpierw podstawowy punkt końcowy, a następnie bezpieczny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1b9c2-117">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="1b9c2-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1b9c2-118">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1b9c2-119">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1b9c2-120">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b9c2-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1b9c2-121">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1b9c2-122">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1b9c2-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b9c2-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1b9c2-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
