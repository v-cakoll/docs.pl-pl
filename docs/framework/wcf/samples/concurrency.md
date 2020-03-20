---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183934"
---
# <a name="concurrency"></a><span data-ttu-id="1a5dc-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="1a5dc-102">Concurrency</span></span>
<span data-ttu-id="1a5dc-103">Przykład współbieżności pokazuje przy <xref:System.ServiceModel.ServiceBehaviorAttribute> użyciu <xref:System.ServiceModel.ConcurrencyMode> z wyliczenia, który kontroluje, czy wystąpienie usługi przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="1a5dc-104">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="1a5dc-105">W tym przykładzie definiuje `ICalculatorConcurrency`nowy kontrakt, `ICalculator`który dziedziczy po , zapewniając dwie dodatkowe operacje do sprawdzania stanu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="1a5dc-106">Zmieniając ustawienie współbieżności, można zaobserwować zmiany w zachowaniu, uruchamiając klienta.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="1a5dc-107">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="1a5dc-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a5dc-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1a5dc-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="1a5dc-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="1a5dc-110">`Single`: Każde wystąpienie usługi przetwarza po jednym komunikacie naraz.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="1a5dc-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="1a5dc-112">`Multiple`: Każde wystąpienie usługi przetwarza wiele komunikatów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="1a5dc-113">Implementacja usługi musi być bezpieczna dla wątków, aby używać tego trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="1a5dc-114">`Reentrant`: Każde wystąpienie usługi przetwarza jedną wiadomość naraz, ale akceptuje wywołania wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="1a5dc-115">Usługa akceptuje te wywołania tylko wtedy, gdy wywołuje. Reentrant jest wykazane w [concurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="1a5dc-116">Użycie współbieżności jest związane z trybem instancing.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="1a5dc-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing współbieżność nie jest istotne, ponieważ każda wiadomość jest przetwarzana przez nowe wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="1a5dc-118">W <xref:System.ServiceModel.InstanceContextMode.Single> instancing albo <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="1a5dc-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, każdy z trybów współbieżności może być istotne.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="1a5dc-120">Klasa usługi określa zachowanie współbieżności `[ServiceBehavior(ConcurrencyMode=<setting>)]` z atrybutem, jak pokazano w przykładzie kodu, który następuje.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="1a5dc-121">Zmieniając wiersze, które są komentowane, `Single` `Multiple` można eksperymentować z trybów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="1a5dc-122">Pamiętaj, aby odbudować usługę po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="1a5dc-123">W przykładzie <xref:System.ServiceModel.ConcurrencyMode.Multiple> używa współbieżności z <xref:System.ServiceModel.InstanceContextMode.Single> instancing domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="1a5dc-124">Kod klienta został zmodyfikowany w celu użycia asynchronickiego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="1a5dc-125">Dzięki temu klient może wykonywać wiele wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="1a5dc-126">Można zaobserwować różnicę w zachowaniu trybu współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="1a5dc-127">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1a5dc-128">Tryb współbieżności, w obszarze usługi jest wyświetlany, każda operacja jest wywoływana, a następnie wyświetlana jest liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="1a5dc-129">Należy zauważyć, że gdy tryb `Multiple`współbieżności jest , wyniki są zwracane w innej kolejności niż jak zostały wywołane, ponieważ usługa przetwarza wiele komunikatów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="1a5dc-130">Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności, w jakiej zostały wywołane, ponieważ usługa przetwarza każdą wiadomość sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="1a5dc-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a5dc-132">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="1a5dc-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1a5dc-133">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a5dc-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1a5dc-134">Jeśli używasz Svcutil.exe do generowania klienta serwera `/async` proxy, upewnij się, że należy dołączyć tę opcję.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="1a5dc-135">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a5dc-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1a5dc-136">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a5dc-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a5dc-137">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1a5dc-138">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1a5dc-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a5dc-140">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1a5dc-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
