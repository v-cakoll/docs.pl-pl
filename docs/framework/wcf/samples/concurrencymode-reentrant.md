---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183893"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="e899a-102">Procedura wielobieżna ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="e899a-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="e899a-103">W tym przykładzie pokazano konieczność i implikacje przy użyciu ConcurrencyMode.Reentrant w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e899a-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="e899a-104">WspółbieżnośćMode.Reentrant oznacza, że usługa (lub wywołanie zwrotne) przetwarza tylko jedną `ConcurencyMode.Single`wiadomość w danym czasie (analogiczne do ).</span><span class="sxs-lookup"><span data-stu-id="e899a-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="e899a-105">Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation `InstanceContext` (WCF) blokuje przetwarzanie wiadomości, dzięki czemu nie można przetwarzać żadnych innych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e899a-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="e899a-106">W przypadku trybu `InstanceContext` reentrant, jest odblokowany tuż przed usługa wykonuje połączenie wychodzące, umożliwiając w ten sposób kolejne wywołanie (które mogą być ponownie przedstawione, jak pokazano w próbce), aby uzyskać blokadę następnym razem, gdy przychodzi do usługi.</span><span class="sxs-lookup"><span data-stu-id="e899a-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="e899a-107">Aby zademonstrować zachowanie, w przykładzie pokazano, jak klient i usługa może wysyłać wiadomości między sobą przy użyciu umowy dupleksu.</span><span class="sxs-lookup"><span data-stu-id="e899a-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="e899a-108">Zdefiniowana umowa jest kontraktem `Ping` dupleksowym z metodą implementowana `Pong` przez usługę i metodą wywołania zwrotnego implementowana przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e899a-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="e899a-109">Klient wywołuje `Ping` metodę serwera z liczbą znaczników, inicjując w ten sposób wywołanie.</span><span class="sxs-lookup"><span data-stu-id="e899a-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="e899a-110">Usługa sprawdza, czy liczba znaczników nie jest równa 0, `Pong` a następnie wywołuje metodę wywołań zwrotnych podczas zmniejszania liczby znaczników.</span><span class="sxs-lookup"><span data-stu-id="e899a-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="e899a-111">Odbywa się to za pomocą następującego kodu w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e899a-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 Implementacja wywołania `Pong` zwrotnego ma taką `Ping` samą logikę jak implementacja. Oznacza to, że sprawdza, czy liczba znaczników `Ping` nie jest równa zero, a następnie wywołuje metodę na kanale wywołania zwrotnego (w tym przypadku jest to kanał, który został użyty do wysłania oryginalnej `Ping` wiadomości) z liczbą znaczników zmniejszanych o 1. W momencie, gdy liczba znaczników osiągnie 0, metoda zwraca w ten sposób rozpakowywanie wszystkich odpowiedzi z powrotem do pierwszego wywołania wykonanego przez klienta, który zainicjował wywołanie. <span data-ttu-id="e899a-115">Jest to pokazane w implementacji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e899a-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Zarówno `Ping` i `Pong` metody są żądanie/odpowiedź, co oznacza, że pierwsze wywołanie `Ping` nie zwraca, dopóki wywołanie `CallbackChannel<T>.Pong()` zwraca. Na kliencie `Pong` metoda nie może `Ping` powrócić do następnego wywołania, które zostało wykonane zwraca. <span data-ttu-id="e899a-118">Ponieważ zarówno wywołania zwrotnego, jak i usługi musi nawiązać wychodzące wywołania żądania/odpowiedzi, zanim będą mogli odpowiedzieć na oczekujące żądanie, obie implementacje muszą być oznaczone zachowaniem ConcurrencyMode.Reentrant.</span><span class="sxs-lookup"><span data-stu-id="e899a-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e899a-119">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e899a-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e899a-120">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e899a-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e899a-121">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e899a-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e899a-122">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e899a-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e899a-123">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e899a-123">Demonstrates</span></span>  
 <span data-ttu-id="e899a-124">Aby uruchomić przykład, skompiluj projekty klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="e899a-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="e899a-125">Następnie otwórz dwa okna poleceń i \<zmień katalogi na przykładowe>\CS\Service\bin\debug i \<próbkowanie katalogów>\CS\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="e899a-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="e899a-126">Następnie uruchom usługę, `service.exe` wpisując, a następnie wywołaj client.exe z początkową wartością znaczników przekazanych jako argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="e899a-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="e899a-127">Pokazano przykładowe dane wyjściowe dla 10 znaczników.</span><span class="sxs-lookup"><span data-stu-id="e899a-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="e899a-128">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e899a-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e899a-129">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e899a-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e899a-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e899a-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e899a-131">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e899a-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
