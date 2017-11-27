---
title: "Współbieżność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0e6a0db5ee02f96582fe71414b620e1f78c40a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="concurrency"></a><span data-ttu-id="fdcbf-102">Współbieżność</span><span class="sxs-lookup"><span data-stu-id="fdcbf-102">Concurrency</span></span>
<span data-ttu-id="fdcbf-103">Przykład współbieżności demonstruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia, która kontroluje, czy wystąpienie usługi przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="fdcbf-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="fdcbf-105">W tym przykładzie definiuje kontrakt nowe `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, zapewniając dwa dodatkowe operacje dla sprawdzenie stanu usługi współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="fdcbf-106">Zmieniając ustawienie współbieżności, można obserwować zmiany w zachowaniu przez uruchomienie klienta.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="fdcbf-107">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="fdcbf-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdcbf-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fdcbf-109">Dostępne są trzy tryby współbieżności:</span><span class="sxs-lookup"><span data-stu-id="fdcbf-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="fdcbf-110">`Single`: Każde wystąpienie usługi przetwarza jeden komunikat naraz.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="fdcbf-111">Jest to domyślny tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="fdcbf-112">`Multiple`: Każde wystąpienie usługi jednocześnie przetwarza wiele komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="fdcbf-113">Implementacja usługi musi być wielowątkowość ten tryb współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="fdcbf-114">`Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w czasie, ale akceptuje wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="fdcbf-115">Usługa akceptuje tylko tych wywołań, wywołując. Procedura wielobieżna jest przedstawiona w [pomocą właściwości ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="fdcbf-116">Użycie współbieżności jest powiązany z trybu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="fdcbf-117">W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="fdcbf-118">W <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień, albo <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza wiadomości sekwencyjnie lub jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="fdcbf-119">W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień, dowolnym trybie współbieżności mogą być istotne.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="fdcbf-120">Klasa usługi określa zachowanie współbieżności `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="fdcbf-121">Zmieniając wierszy, które są oznaczone jako komentarz, możesz eksperymentować z `Single` i `Multiple` tryby współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="fdcbf-122">Pamiętaj, aby odbudować usługę po zmianie trybu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="fdcbf-123">W przykładzie użyto <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności z <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="fdcbf-124">Kod klienta został zmodyfikowany w celu użycia asynchronicznego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="fdcbf-125">Dzięki temu klient może wykonywać wiele wywołania do usługi bez oczekiwania na odpowiedź między każdym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="fdcbf-126">Można obserwować różnice w zachowaniu tryb współbieżności usługi.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="fdcbf-127">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fdcbf-128">Tryb współbieżności, w którym jest uruchomiona w ramach jest wyświetlany, nosi nazwę każdej operacji, a następnie wyświetlana jest liczba operacji.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="fdcbf-129">Zwróć uwagę, że gdy tryb współbieżności jest `Multiple`, wyniki są zwracane w innym porządku niż jak były nazywane, ponieważ usługa przetwarza wiele komunikatów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="fdcbf-130">Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności ich były nazywane, ponieważ usługa przetwarza każdy komunikat po kolei.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="fdcbf-131">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fdcbf-132">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="fdcbf-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fdcbf-133">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdcbf-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fdcbf-134">Jeśli używasz Svcutil.exe do generowania klienta serwera proxy, upewnij się, że obejmuje `/async` opcji.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="fdcbf-135">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdcbf-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="fdcbf-136">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fdcbf-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fdcbf-137">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fdcbf-138">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fdcbf-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fdcbf-139">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fdcbf-140">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fdcbf-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="fdcbf-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdcbf-141">See Also</span></span>
