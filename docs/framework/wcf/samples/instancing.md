---
title: Tworzenie wystąpienia
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1d193b0cac56f365a4f0a294145369502754a1b1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696591"
---
# <a name="instancing"></a><span data-ttu-id="ee0e2-102">Tworzenie wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ee0e2-102">Instancing</span></span>
<span data-ttu-id="ee0e2-103">Przykład Instancing pokazuje ustawienie zachowania wystąpień, które kontroluje sposób tworzenia wystąpienia klasy usługi w odpowiedzi na żądania klientów.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="ee0e2-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="ee0e2-105">Ta przykładowa aplikacja definiuje kontrakt nowe `ICalculatorInstance`, który dziedziczy z `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="ee0e2-106">Kontrakt określony przez `ICalculatorInstance` zawiera trzy dodatkowych operacji sprawdzania stanu wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="ee0e2-107">Zmieniając ustawienie wystąpień, można obserwować zmiany w zachowaniu przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="ee0e2-108">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee0e2-109">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee0e2-110">Dostępne są następujące tryby wystąpień:</span><span class="sxs-lookup"><span data-stu-id="ee0e2-110">The following instancing modes are available:</span></span>  
  
-   <span data-ttu-id="ee0e2-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowe wystąpienie usługi jest tworzona dla każdego żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
-   <span data-ttu-id="ee0e2-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowe wystąpienie jest tworzone dla każdej nowej sesji klienta i utrzymywana ze względu na okres istnienia sesji (wymaga powiązanie, które obsługuje sesji).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
-   <span data-ttu-id="ee0e2-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Jedno wystąpienie klasy usługi obsługuje wszystkie żądania klienta przez okres istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="ee0e2-114">Klasa usługi określa zachowanie wystąpień z `[ServiceBehavior(InstanceContextMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="ee0e2-115">Zmieniając wierszy, które są oznaczone jako komentarz, możesz przyjrzeć się zachowaniu trybach wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="ee0e2-116">Pamiętaj, aby odbudować usługi po zmianie trybu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="ee0e2-117">Nie istnieją żadne ustawienia związane z wystąpień, aby określić na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="ee0e2-118">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ee0e2-119">Tryb wystąpienia, w którym jest uruchomiona w obszarze są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="ee0e2-120">Po zakończeniu każdej operacji liczba wystąpień Identyfikatora i operacji są wyświetlane do odzwierciedlenia zachowanie trybu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="ee0e2-121">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee0e2-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="ee0e2-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee0e2-123">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ee0e2-124">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ee0e2-125">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee0e2-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee0e2-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ee0e2-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee0e2-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee0e2-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee0e2-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a><span data-ttu-id="ee0e2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee0e2-130">See Also</span></span>
