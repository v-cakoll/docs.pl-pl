---
title: Tworzenie wystąpienia
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: d348bd7961eec69663cf6d9b2b7747b7a5800bb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144646"
---
# <a name="instancing"></a><span data-ttu-id="04e04-102">Tworzenie wystąpienia</span><span class="sxs-lookup"><span data-stu-id="04e04-102">Instancing</span></span>
<span data-ttu-id="04e04-103">Przykład Instancing pokazuje ustawienie zachowania instancing, które kontroluje sposób tworzenia wystąpień klasy usługi w odpowiedzi na żądania klientów.</span><span class="sxs-lookup"><span data-stu-id="04e04-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="04e04-104">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="04e04-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="04e04-105">W tym przykładzie zdefiniowano nową umowę, `ICalculatorInstance`która dziedziczy po `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="04e04-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="04e04-106">Umowa określona `ICalculatorInstance` przez zapewnia trzy dodatkowe operacje do sprawdzania stanu wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="04e04-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="04e04-107">Zmieniając ustawienie instancing, można zaobserwować zmianę w zachowaniu, uruchamiając klienta.</span><span class="sxs-lookup"><span data-stu-id="04e04-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="04e04-108">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="04e04-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04e04-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="04e04-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="04e04-110">Dostępne są następujące tryby instancingu:</span><span class="sxs-lookup"><span data-stu-id="04e04-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="04e04-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Dla każdego żądania klienta jest tworzone nowe wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="04e04-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="04e04-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowe wystąpienie jest tworzone dla każdej nowej sesji klienta i utrzymywane przez cały okres istnienia tej sesji (wymaga powiązania, które obsługuje sesję).</span><span class="sxs-lookup"><span data-stu-id="04e04-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="04e04-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Pojedyncze wystąpienie klasy usługi obsługuje wszystkie żądania klienta przez cały okres istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04e04-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="04e04-114">Klasa service określa zachowanie instancing `[ServiceBehavior(InstanceContextMode=<setting>)]` z atrybutem, jak pokazano w przykładzie kodu, który następuje.</span><span class="sxs-lookup"><span data-stu-id="04e04-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="04e04-115">Zmieniając wiersze, które są komentowane, można obserwować zachowanie każdego z trybów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="04e04-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="04e04-116">Pamiętaj, aby odbudować usługę po zmianie trybu instancing.</span><span class="sxs-lookup"><span data-stu-id="04e04-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="04e04-117">Nie ma żadnych ustawień związanych z instancing do określenia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="04e04-117">There are no instancing-related settings to specify on the client.</span></span>  
  
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
  
 <span data-ttu-id="04e04-118">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="04e04-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="04e04-119">Zostanie wyświetlony tryb wystąpienia, w ramach w tym usługa.</span><span class="sxs-lookup"><span data-stu-id="04e04-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="04e04-120">Po każdej operacji identyfikator wystąpienia i liczba operacji są wyświetlane w celu odzwierciedlenia zachowania trybu instancing.</span><span class="sxs-lookup"><span data-stu-id="04e04-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="04e04-121">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="04e04-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="04e04-122">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="04e04-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="04e04-123">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04e04-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="04e04-124">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04e04-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="04e04-125">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04e04-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04e04-126">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="04e04-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04e04-127">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="04e04-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="04e04-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="04e04-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04e04-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="04e04-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
