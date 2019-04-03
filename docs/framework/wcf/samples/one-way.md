---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: e4b8a805fdbe4f330496233d5234abc0169b8c6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826694"
---
# <a name="one-way"></a><span data-ttu-id="3960f-102">Komunikacja jednokierunkowa</span><span class="sxs-lookup"><span data-stu-id="3960f-102">One-Way</span></span>
<span data-ttu-id="3960f-103">Niniejszy przykład pokazuje usługi skontaktuj się z operacji usługi jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="3960f-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="3960f-104">Klient nie czeka na zakończenie, jak w przypadku operacji dwukierunkowe usługi przy użyciu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3960f-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="3960f-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i używa `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="3960f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="3960f-106">Usługi w tym przykładzie to aplikacja konsoli Self-Hosted umożliwia obserwowanie usługa, która odbiera i przetwarza żądania.</span><span class="sxs-lookup"><span data-stu-id="3960f-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="3960f-107">Klient jest również Aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="3960f-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3960f-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3960f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3960f-109">Aby utworzyć kontrakt usługi jednokierunkowej, definiowanie kontraktu usługi, usługi, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, a następnie ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> do `true` jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="3960f-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="3960f-110">Aby zademonstrować, że klient nie czeka na zakończenie operacji usługi, kod usługi, w tym przykładzie implementuje pięciu sekund opóźnienia, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="3960f-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="3960f-111">Gdy klient wywołuje usługę, wywołanie zwraca bez oczekiwania na zakończenie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3960f-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="3960f-112">Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="3960f-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3960f-113">Możesz zobaczyć komunikaty odbierania usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="3960f-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3960f-114">Naciśnij klawisz ENTER w każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="3960f-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="3960f-115">Klient zakończy się wcześniej usługi, prezentacja, że klient nie czeka na zakończenie operacji usługi jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="3960f-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="3960f-116">Dane wyjściowe klienta jest następujący:</span><span class="sxs-lookup"><span data-stu-id="3960f-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3960f-117">Następujące dane wyjściowe usługi jest wyświetlany:</span><span class="sxs-lookup"><span data-stu-id="3960f-117">The following service output is shown:</span></span>  
  
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
>  <span data-ttu-id="3960f-118">Zgodnie z definicją, HTTP jest protokół żądanie/odpowiedź; Po wysłaniu żądania, odpowiedź jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="3960f-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="3960f-119">Ta zasada obowiązuje nawet w przypadku operacji usługi jednokierunkowej, który jest dostępny za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3960f-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="3960f-120">Po wywołaniu operacji usługa zwraca kod stanu HTTP 202, zanim została wykonana operacja usługi.</span><span class="sxs-lookup"><span data-stu-id="3960f-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="3960f-121">Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetwarzania, ale przetwarzanie nie zostało jeszcze zakończone.</span><span class="sxs-lookup"><span data-stu-id="3960f-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="3960f-122">Klient, który wywołał operację blokuje, dopóki nie odbierze odpowiedzi 202 z usługi.</span><span class="sxs-lookup"><span data-stu-id="3960f-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="3960f-123">Może to spowodować niektóre nieoczekiwane zachowanie, gdy wiele jednokierunkowe komunikaty są wysyłane przy użyciu powiązania, który jest skonfigurowany do używania sesji.</span><span class="sxs-lookup"><span data-stu-id="3960f-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="3960f-124">`wsHttpBinding` Powiązania używanego w tym przykładzie jest skonfigurowany do używania sesji, aby domyślnie ustanawiania kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3960f-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="3960f-125">Domyślnie komunikaty w sesji dotrą do celu w kolejności, w której są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="3960f-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="3960f-126">W związku z tym gdy drugi komunikat w sesji są wysyłane, nie został przetworzony aż pierwszy komunikat został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="3960f-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="3960f-127">Z tego powodu jest, że klient nie otrzyma odpowiedzi 202 wiadomości do momentu zakończenia przetwarzania poprzedni komunikat.</span><span class="sxs-lookup"><span data-stu-id="3960f-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="3960f-128">Klient w związku z tym wydaje się blok przy każdym wywołaniu kolejna operacja.</span><span class="sxs-lookup"><span data-stu-id="3960f-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="3960f-129">Aby uniknąć tego zachowania, ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego do wysyłania komunikatów jednocześnie w celu odrębnych wystąpień do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="3960f-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="3960f-130">Przykładowe zestawy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> do `PerCall` tak, aby każdy komunikat mogą być przetwarzane przez inne wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="3960f-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="3960f-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ustawiono `Multiple` umożliwia więcej niż jeden wątek do wysyłania wiadomości w czasie.</span><span class="sxs-lookup"><span data-stu-id="3960f-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3960f-132">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="3960f-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3960f-133">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3960f-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3960f-134">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3960f-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3960f-135">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3960f-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3960f-136">Przed uruchomieniem klienta i zamknąć klienta przed zamknięciem usługi, należy uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="3960f-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="3960f-137">Umożliwia to uniknięcie wyjątek klienta, gdy klient nie można zamknąć sesji zabezpieczeń nie pozostawia żadnych śladów, ponieważ usługa został usunięty.</span><span class="sxs-lookup"><span data-stu-id="3960f-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3960f-138">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3960f-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3960f-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3960f-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3960f-140">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3960f-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3960f-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3960f-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
