---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 07fc4ecf981acbad577758c943aa22405f528a52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575255"
---
# <a name="one-way"></a><span data-ttu-id="4e39d-102">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="4e39d-102">One-Way</span></span>
<span data-ttu-id="4e39d-103">Ten przykład pokazuje kontakt z usługą z jednokierunkowymi operacjami usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="4e39d-104">Klient nie czeka na zakończenie operacji usługi, podobnie jak w przypadku operacji dwukierunkowych usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="4e39d-105">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) i używa `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="4e39d-105">This sample is based on the [Getting Started](getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="4e39d-106">Usługa w tym przykładzie to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi, która odbiera i przetwarza żądania.</span><span class="sxs-lookup"><span data-stu-id="4e39d-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="4e39d-107">Klient jest również aplikacją konsolową.</span><span class="sxs-lookup"><span data-stu-id="4e39d-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e39d-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4e39d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4e39d-109">Aby utworzyć kontrakt usługi jednokierunkowej, zdefiniuj kontrakt usługi, Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji i ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` tak, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4e39d-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="4e39d-110">Aby zademonstrować, że klient nie czeka na zakończenie operacji usługi, kod usługi w tym przykładzie implementuje pięć-sekundowe opóźnienie, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4e39d-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="4e39d-111">Gdy klient wywołuje usługę, wywołanie zwraca bez oczekiwania na zakończenie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="4e39d-112">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4e39d-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4e39d-113">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="4e39d-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="4e39d-114">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="4e39d-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="4e39d-115">Klient kończy pracę przed usługą, pokazując, że klient nie czeka na zakończenie operacji jednokierunkowej usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="4e39d-116">Dane wyjściowe klienta są następujące:</span><span class="sxs-lookup"><span data-stu-id="4e39d-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4e39d-117">Wyświetlane są następujące dane wyjściowe usługi:</span><span class="sxs-lookup"><span data-stu-id="4e39d-117">The following service output is shown:</span></span>  
  
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
> <span data-ttu-id="4e39d-118">HTTP to, według definicji, protokołu żądania/odpowiedzi; Po wykonaniu żądania zwracana jest odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4e39d-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="4e39d-119">Jest to prawdziwe nawet dla jednokierunkowej operacji usługi, która jest udostępniona za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e39d-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="4e39d-120">Po wywołaniu operacji usługa zwraca kod stanu HTTP 202 przed wykonaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="4e39d-121">Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetworzenia, ale przetwarzanie nie zostało jeszcze zakończone.</span><span class="sxs-lookup"><span data-stu-id="4e39d-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="4e39d-122">Klient, który wywołał bloki operacji, dopóki nie odbierze odpowiedzi 202 od usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="4e39d-123">Może to spowodować pewne nieoczekiwane zachowanie, gdy wiele komunikatów jednokierunkowych jest wysyłanych przy użyciu powiązania, które jest skonfigurowane do korzystania z sesji.</span><span class="sxs-lookup"><span data-stu-id="4e39d-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="4e39d-124">`wsHttpBinding`Powiązanie używane w tym przykładzie jest skonfigurowane tak, aby domyślnie używać sesji w celu ustanowienia kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4e39d-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="4e39d-125">Domyślnie komunikaty w sesji są gwarantowane w kolejności, w jakiej są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="4e39d-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="4e39d-126">W związku z tym, gdy wysyłany jest drugi komunikat w sesji, nie jest przetwarzany do momentu przetworzenia pierwszego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4e39d-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="4e39d-127">Wynika to z tego, że klient nie otrzymuje odpowiedzi 202 na komunikat do momentu ukończenia przetwarzania poprzedniego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4e39d-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="4e39d-128">W związku z tym klient jest blokowany dla każdego kolejnego wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="4e39d-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="4e39d-129">Aby uniknąć tego zachowania, ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego do wysyłania komunikatów współbieżnie do różnych wystąpień do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="4e39d-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="4e39d-130">Przykład ustawia <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> się `PerCall` tak, aby każdy komunikat mógł być przetwarzany przez inne wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="4e39d-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="4e39d-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>jest ustawiona na tak, aby `Multiple` umożliwić wysyłanie komunikatów jednocześnie więcej niż jeden wątek.</span><span class="sxs-lookup"><span data-stu-id="4e39d-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e39d-132">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4e39d-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e39d-133">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e39d-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4e39d-134">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e39d-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4e39d-135">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e39d-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e39d-136">Uruchom usługę przed uruchomieniem klienta i wyłącz klienta przed zamknięciem usługi.</span><span class="sxs-lookup"><span data-stu-id="4e39d-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="4e39d-137">Pozwala to uniknąć wyjątku klienta, gdy klient nie może prawidłowo zamknąć sesji zabezpieczeń, ponieważ usługa zniknęła.</span><span class="sxs-lookup"><span data-stu-id="4e39d-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4e39d-138">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4e39d-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e39d-139">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4e39d-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4e39d-140">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4e39d-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e39d-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4e39d-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
