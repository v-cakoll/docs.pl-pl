---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 17cad01dfd0474c2c0520987ba45445a256f72b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505039"
---
# <a name="concurrency"></a><span data-ttu-id="e3836-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="e3836-102">Concurrency</span></span>
<span data-ttu-id="e3836-103">Przykład współbieżności demonstruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia, która kontroluje, czy wystąpienie usługi przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e3836-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e3836-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e3836-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e3836-105">W tym przykładzie definiuje kontrakt nowe `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, zapewniając dwa dodatkowe operacje dla sprawdzenie stanu usługi współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e3836-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="e3836-106">Zmieniając ustawienie współbieżności, można obserwować zmiany w zachowaniu przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="e3836-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="e3836-107">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e3836-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3836-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e3836-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e3836-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="e3836-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="e3836-110">`Single`: Każde wystąpienie usługi przetwarza jeden komunikat naraz.</span><span class="sxs-lookup"><span data-stu-id="e3836-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="e3836-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e3836-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="e3836-112">`Multiple`: Każde wystąpienie usługi jednocześnie przetwarza wiele komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e3836-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="e3836-113">Implementacja usługi musi być wielowątkowość ten tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e3836-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="e3836-114">`Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w czasie, ale akceptuje wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="e3836-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="e3836-115">Usługa akceptuje tylko tych wywołań, wywołując. Procedura wielobieżna jest przedstawiona w [pomocą właściwości ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="e3836-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="e3836-116">Użycie współbieżności jest powiązany z trybu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e3836-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="e3836-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e3836-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="e3836-118">W <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień, albo <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e3836-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e3836-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień, dowolnym trybie współbieżności mogą być istotne.</span><span class="sxs-lookup"><span data-stu-id="e3836-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="e3836-120">Klasa usługi określa zachowanie współbieżności `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e3836-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="e3836-121">Zmieniając wierszy, które są oznaczone jako komentarz, możesz eksperymentować z `Single` i `Multiple` tryby współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e3836-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="e3836-122">Pamiętaj, aby odbudować usługę po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e3836-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="e3836-123">W przykładzie użyto <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności z <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3836-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="e3836-124">Kod klienta został zmodyfikowany w celu użycia asynchronicznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e3836-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="e3836-125">Dzięki temu klient może wykonywać wiele wywołania do usługi bez oczekiwania na odpowiedź między każdym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="e3836-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="e3836-126">Można obserwować różnice w zachowaniu tryb współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="e3836-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="e3836-127">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e3836-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e3836-128">Tryb współbieżności, w którym jest uruchomiona w ramach jest wyświetlany, nosi nazwę każdej operacji, a następnie wyświetlana jest liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="e3836-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="e3836-129">Zwróć uwagę, że gdy tryb współbieżności jest `Multiple`, wyniki są zwracane w innym porządku niż jak były nazywane, ponieważ usługa przetwarza wiele komunikatów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e3836-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="e3836-130">Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności ich były nazywane, ponieważ usługa przetwarza każdy komunikat po kolei.</span><span class="sxs-lookup"><span data-stu-id="e3836-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="e3836-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e3836-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3836-132">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="e3836-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e3836-133">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3836-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e3836-134">Jeśli używasz Svcutil.exe do generowania klienta serwera proxy, upewnij się, że obejmuje `/async` opcji.</span><span class="sxs-lookup"><span data-stu-id="e3836-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="e3836-135">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3836-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e3836-136">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3836-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3836-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e3836-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3836-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e3836-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3836-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e3836-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3836-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e3836-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="e3836-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3836-141">See Also</span></span>
