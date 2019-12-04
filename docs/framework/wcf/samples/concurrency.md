---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 1342e50a5dca56260f832f5e0d684f4f79d355e2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715992"
---
# <a name="concurrency"></a><span data-ttu-id="5d035-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="5d035-102">Concurrency</span></span>
<span data-ttu-id="5d035-103">Przykład współbieżności ilustruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> z wyliczeniem <xref:System.ServiceModel.ConcurrencyMode>, które określa, czy wystąpienie usługi przetwarza komunikaty sekwencyjnie czy współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="5d035-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="5d035-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje kontrakt usługi `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="5d035-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5d035-105">Ten przykład definiuje nowy kontrakt, `ICalculatorConcurrency`, który dziedziczy po `ICalculator`, zapewniając dwie dodatkowe operacje do sprawdzania stanu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="5d035-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="5d035-106">Zmieniając ustawienie współbieżności, można obserwować zmianę zachowania przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="5d035-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="5d035-107">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5d035-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d035-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5d035-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5d035-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="5d035-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="5d035-110">`Single`: każde wystąpienie usługi przetwarza jeden komunikat w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="5d035-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="5d035-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5d035-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="5d035-112">`Multiple`: każde wystąpienie usługi przetwarza wiele komunikatów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="5d035-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="5d035-113">Implementacja usługi musi być bezpieczna wątkowo, aby można było używać tego trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5d035-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="5d035-114">`Reentrant`: każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="5d035-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="5d035-115">Usługa akceptuje te wywołania tylko wtedy, gdy jest wywoływany. Reprezentacja jest przedstawiona w przykładzie [concurrency.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) Retail.</span><span class="sxs-lookup"><span data-stu-id="5d035-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="5d035-116">Użycie współbieżności jest związane z trybem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5d035-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="5d035-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> tworzenia wystąpienia współbieżność nie jest istotna, ponieważ każdy komunikat jest przetwarzany przez nowe wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="5d035-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="5d035-118">W <xref:System.ServiceModel.InstanceContextMode.Single> tworzeniu wystąpienia <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżność jest istotna, w zależności od tego, czy pojedyncze wystąpienie przetwarza komunikaty sekwencyjnie czy współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="5d035-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="5d035-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpieniach mogą być odpowiednie wszystkie tryby współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5d035-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="5d035-120">Klasa usługi określa zachowanie współbieżności z atrybutem `[ServiceBehavior(ConcurrencyMode=<setting>)]`, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5d035-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="5d035-121">Poprzez zmianę wierszy, które są oznaczone jako komentarze, można eksperymentować z `Single` i `Multiple` trybów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5d035-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="5d035-122">Pamiętaj, aby ponownie skompilować usługę po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5d035-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5d035-123">Przykład domyślnie używa <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności z wystąpieniami <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="5d035-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="5d035-124">Kod klienta został zmodyfikowany w celu korzystania z asynchronicznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5d035-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="5d035-125">Dzięki temu Klient może wykonywać wiele wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="5d035-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="5d035-126">Można obserwować różnicę w działaniu trybu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="5d035-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="5d035-127">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5d035-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5d035-128">Zostanie wyświetlona opcja tryb współbieżności, w którym jest uruchomiona usługa, każda operacja jest wywoływana, a następnie wyświetlana jest liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="5d035-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="5d035-129">Należy zauważyć, że gdy tryb współbieżności jest `Multiple`, wyniki są zwracane w innej kolejności niż w przypadku ich wywołania, ponieważ usługa przetwarza wiele komunikatów współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="5d035-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="5d035-130">Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności, w jakiej zostały wywołane, ponieważ usługa przetwarza każdy komunikat sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="5d035-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="5d035-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="5d035-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d035-132">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5d035-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5d035-133">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d035-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5d035-134">Jeśli używasz programu Svcutil. exe do generowania klienta proxy, upewnij się, że dołączysz opcję `/async`.</span><span class="sxs-lookup"><span data-stu-id="5d035-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="5d035-135">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d035-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5d035-136">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d035-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d035-137">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5d035-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d035-138">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5d035-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5d035-139">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d035-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d035-140">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5d035-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
