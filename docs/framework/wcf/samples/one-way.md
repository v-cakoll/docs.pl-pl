---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183441"
---
# <a name="one-way"></a><span data-ttu-id="7a83b-102">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="7a83b-102">One-Way</span></span>
<span data-ttu-id="7a83b-103">W tym przykładzie pokazano kontakt usługi z jednokierunkowych operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7a83b-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="7a83b-104">Klient nie czeka na zakończenie operacji usługi, jak ma to miejsce w przypadku operacji usługi dwukierunkowej.</span><span class="sxs-lookup"><span data-stu-id="7a83b-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="7a83b-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) `wsHttpBinding` i używa powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a83b-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="7a83b-106">Usługa w tym przykładzie jest samodzielną aplikacją konsoli, aby umożliwić obserwowanie usługi, która odbiera i przetwarza żądania.</span><span class="sxs-lookup"><span data-stu-id="7a83b-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="7a83b-107">Klient jest również aplikacją konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a83b-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a83b-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7a83b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7a83b-109">Aby utworzyć jednokierunkową umowę serwisową, zdefiniuj umowę serwisową, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` ustaw, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7a83b-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="7a83b-110">Aby wykazać, że klient nie czeka na zakończenie operacji usługi, kod usługi w tym przykładzie implementuje opóźnienie pięciu sekund, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7a83b-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="7a83b-111">Gdy klient wywołuje usługę, wywołanie zwraca bez oczekiwania na zakończenie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7a83b-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="7a83b-112">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="7a83b-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="7a83b-113">Możesz zobaczyć, że usługa odbiera wiadomości od klienta.</span><span class="sxs-lookup"><span data-stu-id="7a83b-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="7a83b-114">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć zarówno usługę, jak i klienta.</span><span class="sxs-lookup"><span data-stu-id="7a83b-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="7a83b-115">Klient kończy przed usługą, wykazując, że klient nie czeka na zakończenie operacji usługi jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="7a83b-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="7a83b-116">Dane wyjściowe klienta są następujące:</span><span class="sxs-lookup"><span data-stu-id="7a83b-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7a83b-117">Następujące dane wyjściowe usługi są wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="7a83b-117">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> <span data-ttu-id="7a83b-118">PROTOKÓŁ HTTP jest z definicji protokołem żądania/odpowiedzi; po złożeniu żądania zwracana jest odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7a83b-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="7a83b-119">Dotyczy to nawet operacji usługi jednokierunkowej, która jest widoczna za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a83b-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="7a83b-120">Gdy operacja jest wywoływana, usługa zwraca kod stanu HTTP 202 przed wykonaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7a83b-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="7a83b-121">Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetworzenia, ale przetwarzanie nie zostało jeszcze zakończone.</span><span class="sxs-lookup"><span data-stu-id="7a83b-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="7a83b-122">Klient, który wezwał bloki operacji, dopóki nie otrzyma odpowiedzi 202 z usługi.</span><span class="sxs-lookup"><span data-stu-id="7a83b-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="7a83b-123">Może to spowodować pewne nieoczekiwane zachowanie, gdy wiele komunikatów jednokierunkowych są wysyłane przy użyciu powiązania, które jest skonfigurowane do korzystania z sesji.</span><span class="sxs-lookup"><span data-stu-id="7a83b-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="7a83b-124">Powiązanie `wsHttpBinding` używane w tym przykładzie jest skonfigurowane do domyślnego używania sesji w celu ustanowienia kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a83b-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="7a83b-125">Domyślnie wiadomości w sesji są gwarantowane do jść w kolejności, w jakiej są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="7a83b-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="7a83b-126">Z tego powodu po wysłaniu drugiej wiadomości w sesji nie jest przetwarzana, dopóki nie zostanie przetworzona pierwsza wiadomość.</span><span class="sxs-lookup"><span data-stu-id="7a83b-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="7a83b-127">Wynik jest to, że klient nie otrzyma odpowiedzi 202 dla wiadomości, dopóki przetwarzanie poprzedniej wiadomości zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="7a83b-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="7a83b-128">W związku z tym klient wydaje się blokować przy każdym kolejnym wywołaniu operacji.</span><span class="sxs-lookup"><span data-stu-id="7a83b-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="7a83b-129">Aby uniknąć tego zachowania, w tym przykładzie konfiguruje środowisko uruchomieniowe do wysyłania komunikatów jednocześnie do różnych wystąpień do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7a83b-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="7a83b-130">Przykładowy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> zestaw, tak aby `PerCall` każda wiadomość może być przetwarzane przez inne wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7a83b-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="7a83b-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>jest ustawiona, aby `Multiple` zezwolić na więcej niż jeden wątek do wysyłania wiadomości w czasie.</span><span class="sxs-lookup"><span data-stu-id="7a83b-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7a83b-132">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="7a83b-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7a83b-133">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a83b-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7a83b-134">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a83b-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7a83b-135">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a83b-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a83b-136">Uruchom usługę przed uruchomieniem klienta i zamknąć klienta przed zamknięciem usługi.</span><span class="sxs-lookup"><span data-stu-id="7a83b-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="7a83b-137">Pozwala to uniknąć wyjątku klienta, gdy klient nie może zamknąć sesji zabezpieczeń czysto, ponieważ usługa zniknęła.</span><span class="sxs-lookup"><span data-stu-id="7a83b-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7a83b-138">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a83b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a83b-139">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="7a83b-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7a83b-140">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7a83b-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a83b-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7a83b-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
