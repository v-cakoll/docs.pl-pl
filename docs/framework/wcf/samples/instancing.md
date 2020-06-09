---
title: Tworzenie wystąpienia
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1cfaa0db5b81858b733343f17cae71e5815ef60b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596632"
---
# <a name="instancing"></a><span data-ttu-id="ba16b-102">Tworzenie wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ba16b-102">Instancing</span></span>
<span data-ttu-id="ba16b-103">Przykładowa funkcja tworzenia wystąpień pokazuje ustawienie zachowania tworzenia wystąpienia, które określa sposób, w jaki wystąpienie klasy usługi jest tworzone w odpowiedzi na żądania klientów.</span><span class="sxs-lookup"><span data-stu-id="ba16b-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="ba16b-104">Przykład jest oparty na [wprowadzenie](getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="ba16b-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="ba16b-105">Ten przykład definiuje nowy kontrakt, `ICalculatorInstance` który dziedziczy z `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="ba16b-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="ba16b-106">Kontrakt określony przez `ICalculatorInstance` zawiera trzy dodatkowe operacje umożliwiające sprawdzenie stanu wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="ba16b-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="ba16b-107">Zmieniając ustawienie tworzenia wystąpienia, można obserwować zmianę zachowania przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="ba16b-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="ba16b-108">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ba16b-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba16b-109">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ba16b-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ba16b-110">Dostępne są następujące tryby wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="ba16b-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="ba16b-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowe wystąpienie usługi jest tworzone dla każdego żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="ba16b-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="ba16b-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowe wystąpienie jest tworzone dla każdej nowej sesji klienta i utrzymywane przez okres istnienia tej sesji (wymaga powiązania, które obsługuje sesję).</span><span class="sxs-lookup"><span data-stu-id="ba16b-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="ba16b-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Pojedyncze wystąpienie klasy usługi obsługuje wszystkie żądania klientów w okresie istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba16b-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="ba16b-114">Klasa usługi określa zachowanie podczas wystąpienia z `[ServiceBehavior(InstanceContextMode=<setting>)]` atrybutem, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ba16b-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="ba16b-115">Zmieniając wiersze, które są oznaczone jako komentarze, można obserwować zachowanie każdego z trybów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ba16b-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="ba16b-116">Pamiętaj, aby ponownie skompilować usługę po zmianie trybu tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ba16b-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="ba16b-117">Brak ustawień związanych z tworzeniem wystąpień do określenia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="ba16b-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="ba16b-118">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ba16b-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ba16b-119">Zostanie wyświetlona opcja tryb wystąpienia, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="ba16b-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="ba16b-120">Po każdej operacji zostanie wyświetlony komunikat o IDENTYFIKATORze i liczbie operacji odzwierciedlający zachowanie trybu Tworzenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ba16b-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="ba16b-121">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="ba16b-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba16b-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="ba16b-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ba16b-123">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba16b-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ba16b-124">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba16b-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ba16b-125">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba16b-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ba16b-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba16b-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba16b-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="ba16b-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ba16b-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ba16b-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba16b-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ba16b-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
