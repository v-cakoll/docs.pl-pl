---
title: Hostowanie usług IIS przy użyciu kodu wbudowanego
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 304da4fa7d2bb48899cdec864fb2dc1f9fdfb9ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746435"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="d0411-102">Hostowanie usług IIS przy użyciu kodu wbudowanego</span><span class="sxs-lookup"><span data-stu-id="d0411-102">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="d0411-103">Ten przykład ilustruje sposób implementacji usługi hostowanej przez Internet Information Services (IIS), gdzie kod usługi jest zawarty w pliku svc i jest kompilowany na żądanie.</span><span class="sxs-lookup"><span data-stu-id="d0411-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="d0411-104">Kod usługi można również zaimplementować bezpośrednio w plikach kodu źródłowego znajdujących się w katalogu \ App_Code aplikacji lub kompilować do zestawu wdrożonego w \Bin.</span><span class="sxs-lookup"><span data-stu-id="d0411-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="d0411-105">Ten przykład nie pokazuje tych technik.</span><span class="sxs-lookup"><span data-stu-id="d0411-105">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="d0411-106">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d0411-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0411-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d0411-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d0411-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d0411-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d0411-109">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0411-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0411-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d0411-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="d0411-111">W przykładzie pokazano typową usługę, która implementuje kontrakt definiujący wzorzec komunikacji z odpowiedzią na żądanie.</span><span class="sxs-lookup"><span data-stu-id="d0411-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="d0411-112">Usługa jest hostowana w usługach IIS, a kod usługi jest całkowicie zawarty w pliku Service. svc.</span><span class="sxs-lookup"><span data-stu-id="d0411-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="d0411-113">Usługa jest uruchomiona na hoście i skompilowana na żądanie przez pierwszą wiadomość wysłaną do usługi.</span><span class="sxs-lookup"><span data-stu-id="d0411-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="d0411-114">Nie ma potrzeby wstępnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d0411-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="d0411-115">Usługa implementuje kontrakt `ICalculator` zgodnie z definicją w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d0411-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="d0411-116">Implementacja usługi oblicza i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="d0411-116">The service implementation calculates and returns the appropriate result.</span></span>

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="d0411-117">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d0411-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d0411-118">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="d0411-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0411-119">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d0411-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d0411-120">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0411-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d0411-121">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0411-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d0411-122">Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="d0411-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="d0411-123">Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="d0411-123">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="d0411-124">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0411-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="d0411-125">Aby zapoznać się z przykładem dotyczącym tworzenia aplikacji klienckiej, która może wywołać tę usługę, zobacz [How to: Create an Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d0411-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0411-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0411-126">See also</span></span>

- <span data-ttu-id="d0411-127">[Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d0411-127">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
