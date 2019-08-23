---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: ab1cab4cf2c9fb8902eef321bfa7b1a610376771
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969043"
---
# <a name="concurrency"></a><span data-ttu-id="e5d33-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="e5d33-102">Concurrency</span></span>
<span data-ttu-id="e5d33-103">Przykład współbieżności ilustruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.ConcurrencyMode> z wyliczeniem, które określa, czy wystąpienie usługi przetwarza komunikaty sekwencyjnie czy współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="e5d33-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e5d33-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="e5d33-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e5d33-105">Ten przykład definiuje nowy kontrakt `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, dostarczając dwie dodatkowe operacje do sprawdzania stanu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="e5d33-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="e5d33-106">Zmieniając ustawienie współbieżności, można obserwować zmianę zachowania przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="e5d33-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="e5d33-107">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e5d33-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5d33-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e5d33-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e5d33-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="e5d33-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="e5d33-110">`Single`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="e5d33-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="e5d33-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e5d33-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="e5d33-112">`Multiple`: Każde wystąpienie usługi przetwarza jednocześnie wiele komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e5d33-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="e5d33-113">Implementacja usługi musi być bezpieczna wątkowo, aby można było używać tego trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e5d33-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="e5d33-114">`Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="e5d33-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="e5d33-115">Usługa akceptuje te wywołania tylko wtedy, gdy jest wywoływany. Reprezentacja jest przedstawiona w przykładzie [concurrency.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) Retail.</span><span class="sxs-lookup"><span data-stu-id="e5d33-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="e5d33-116">Użycie współbieżności jest związane z trybem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e5d33-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="e5d33-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> przypadku tworzenia wystąpień współbieżność nie jest istotna, ponieważ każdy komunikat jest przetwarzany przez nowe wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="e5d33-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="e5d33-118">W <xref:System.ServiceModel.InstanceContextMode.Single> przypadkuwystąpienia<xref:System.ServiceModel.ConcurrencyMode.Multiple> , w zależności od tego, czy pojedyncze wystąpienie przetwarza komunikaty sekwencyjnie, czy współbieżnie. <xref:System.ServiceModel.ConcurrencyMode.Single></span><span class="sxs-lookup"><span data-stu-id="e5d33-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e5d33-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> przypadku wystąpienia może być istotny dowolny z trybów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e5d33-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="e5d33-120">Klasa usługi określa zachowanie współbieżności z `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutem, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e5d33-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="e5d33-121">Poprzez zmianę wierszy, które są oznaczone jako komentarze, można eksperymentować `Single` z `Multiple` trybami współbieżności i.</span><span class="sxs-lookup"><span data-stu-id="e5d33-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="e5d33-122">Pamiętaj, aby ponownie skompilować usługę po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e5d33-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="e5d33-123">Przykład domyślnie używa <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności <xref:System.ServiceModel.InstanceContextMode.Single> z wystąpieniami.</span><span class="sxs-lookup"><span data-stu-id="e5d33-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="e5d33-124">Kod klienta został zmodyfikowany w celu korzystania z asynchronicznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e5d33-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="e5d33-125">Dzięki temu Klient może wykonywać wiele wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="e5d33-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="e5d33-126">Można obserwować różnicę w działaniu trybu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="e5d33-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="e5d33-127">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e5d33-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e5d33-128">Zostanie wyświetlona opcja tryb współbieżności, w którym jest uruchomiona usługa, każda operacja jest wywoływana, a następnie wyświetlana jest liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="e5d33-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="e5d33-129">Należy zauważyć, że gdy tryb współbieżności to `Multiple`, wyniki są zwracane w innej kolejności niż w sposobie ich wywołania, ponieważ usługa przetwarza wiele komunikatów współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="e5d33-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="e5d33-130">Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności, w jakiej zostały wywołane, ponieważ usługa przetwarza każdy komunikat sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="e5d33-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="e5d33-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="e5d33-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e5d33-132">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e5d33-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e5d33-133">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5d33-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e5d33-134">Jeśli używasz programu Svcutil. exe do generowania klienta proxy, upewnij się, że dołączysz `/async` opcję.</span><span class="sxs-lookup"><span data-stu-id="e5d33-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="e5d33-135">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5d33-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e5d33-136">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e5d33-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5d33-137">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5d33-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e5d33-138">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e5d33-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e5d33-139">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e5d33-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5d33-140">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5d33-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
