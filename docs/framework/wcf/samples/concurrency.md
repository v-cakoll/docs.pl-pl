---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 892def5d9788dfdf86d312aa04cf89e891323971
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528430"
---
# <a name="concurrency"></a><span data-ttu-id="e32b6-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="e32b6-102">Concurrency</span></span>
<span data-ttu-id="e32b6-103">Przykład współbieżności, który demonstruje sposób użycia <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia, które kontrolują, czy wystąpienie usługi przetwarza komunikaty kolejno lub równolegle.</span><span class="sxs-lookup"><span data-stu-id="e32b6-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e32b6-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e32b6-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e32b6-105">Ta przykładowa aplikacja definiuje kontrakt nowe `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, zapewniając dwóch dodatkowych operacji sprawdzania stanu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="e32b6-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="e32b6-106">Zmieniając ustawienie współbieżności, można obserwować zmiany w zachowaniu przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="e32b6-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="e32b6-107">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="e32b6-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e32b6-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e32b6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e32b6-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="e32b6-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="e32b6-110">`Single`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="e32b6-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="e32b6-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e32b6-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="e32b6-112">`Multiple`: Każde wystąpienie usługi przetwarza wiele wiadomości jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e32b6-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="e32b6-113">Implementacja usługi musi być wątków, aby użyć tego trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e32b6-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="e32b6-114">`Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="e32b6-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="e32b6-115">Usługa akceptuje tylko te wywołania kontaktujący. Wielobieżna ConcurrencyMode została przedstawiona w [pomocą właściwości ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="e32b6-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="e32b6-116">Użycie współbieżności jest powiązana z trybu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e32b6-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="e32b6-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowe wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="e32b6-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="e32b6-118">W <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień, albo <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżność jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza komunikaty kolejno lub równolegle.</span><span class="sxs-lookup"><span data-stu-id="e32b6-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e32b6-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień, jednym z trybów współbieżności mogą być istotne.</span><span class="sxs-lookup"><span data-stu-id="e32b6-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="e32b6-120">Klasa usługi określa zachowanie współbieżności przy użyciu `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e32b6-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="e32b6-121">Zmieniając wierszy, które są oznaczone jako komentarz, możesz eksperymentować z `Single` i `Multiple` tryby współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e32b6-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="e32b6-122">Pamiętaj, aby odbudować usługi po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e32b6-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```  
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="e32b6-123">W przykładzie użyto <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności przy użyciu <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e32b6-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="e32b6-124">Kod klienta została zmodyfikowana, aby używać asynchronicznych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e32b6-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="e32b6-125">Dzięki temu klientowi skierowanie wielu wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="e32b6-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="e32b6-126">Możesz obserwować różnicy w zachowaniu trybu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="e32b6-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="e32b6-127">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e32b6-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e32b6-128">Tryb współbieżności, w którym działa usługa jest wyświetlana, nosi nazwę każdej operacji i następnie jest wyświetlana liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="e32b6-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="e32b6-129">Należy zauważyć, że przy włączonym trybie współbieżności `Multiple`, wyniki są zwracane w kolejności innej niż jak zostały wywołane, ponieważ usługa przetwarza wiele wiadomości jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e32b6-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="e32b6-130">Zmieniając tryb współbieżności `Single`, wyniki są zwracane w kolejności ich wywołane, ponieważ usługa przetwarza każdy komunikat sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="e32b6-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="e32b6-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e32b6-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e32b6-132">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="e32b6-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e32b6-133">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b6-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e32b6-134">Korzystając z programu Svcutil.exe do generowania klienta serwera proxy, upewnij się, że zawrzesz `/async` opcji.</span><span class="sxs-lookup"><span data-stu-id="e32b6-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="e32b6-135">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b6-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e32b6-136">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32b6-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e32b6-137">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e32b6-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e32b6-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e32b6-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e32b6-139">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e32b6-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e32b6-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e32b6-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="e32b6-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e32b6-141">See Also</span></span>
