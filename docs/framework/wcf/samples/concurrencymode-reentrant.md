---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c6bb73957da055e9d867fbcb78ce78acdb8d0b76
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040144"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="21983-102">Procedura wielobieżna ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="21983-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="21983-103">Ten przykład pokazuje konieczność i implikacje użycia ConcurrencyMode. using w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="21983-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="21983-104">Concurrency. repodmiotu oznacza, że usługa (lub wywołania zwrotne) przetwarza tylko jeden komunikat w danym momencie (analogicznie do `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="21983-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="21983-105">Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation (WCF) blokuje `InstanceContext` przetwarzanie komunikatu, aby nie można było przetworzyć innych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="21983-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="21983-106">W przypadku trybu przechodzenia, `InstanceContext` jest odblokowany tuż przed wykonaniem wywołania wychodzącego przez usługę, co pozwala na kolejne wywołanie (które może być w sposób pokazany w przykładzie), aby uzyskać blokadę po następnym przejściu do usługi.</span><span class="sxs-lookup"><span data-stu-id="21983-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="21983-107">Aby zademonstrować zachowanie, przykład pokazuje, jak klient i usługa mogą wysyłać komunikaty między sobą przy użyciu kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="21983-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="21983-108">Zdefiniowany kontrakt jest umową dupleksową z `Ping` metodą implementowaną przez usługę i metodę `Pong` wywołania zwrotnego implementowaną przez klienta.</span><span class="sxs-lookup"><span data-stu-id="21983-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="21983-109">Klient wywołuje `Ping` metodę serwera z liczbą cyklów, co spowoduje zainicjowanie wywołania.</span><span class="sxs-lookup"><span data-stu-id="21983-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="21983-110">Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje `Pong` metodę wywołania zwrotnego przy zmniejszeniu liczby taktów.</span><span class="sxs-lookup"><span data-stu-id="21983-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="21983-111">Jest to realizowane przez Poniższy kod w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="21983-111">This is done by the following code in the sample.</span></span>  
  
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
  
 `Pong` Implementacja wywołania zwrotnego ma taką samą logikę `Ping` jak implementacja. Oznacza to, że sprawdza, czy liczba cykli nie jest równa zero, `Ping` a następnie wywołuje metodę w kanale wywołania zwrotnego (w tym przypadku jest to kanał, który został użyty `Ping` do wysłania oryginalnej wiadomości) z liczbą cykli równą 1. Moment, w którym licznik taktu osiągnie wartość 0, metoda zwraca w ten sposób odpakowanie wszystkich odpowiedzi z powrotem do pierwszego wywołania wykonanego przez klienta, który zainicjował wywołanie. <span data-ttu-id="21983-115">Jest to pokazane w implementacji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="21983-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Obie metody `Pong` `Ping` i są żądaniami/odpowiedzi, co oznacza, że pierwsze wywołanie nie zwraca do momentu wywołania `CallbackChannel<T>.Pong()` zwrotnego. `Ping` Na kliencie `Pong` Metoda nie może zwrócić do momentu następnego `Ping` wywołania, które wykona. <span data-ttu-id="21983-118">Ponieważ zarówno wywołanie zwrotne, jak i usługa muszą wychodzące wywołania żądania/odpowiedzi, zanim będą mogły odpowiedzieć na oczekujące żądanie, obie implementacje muszą być oznaczone jako takie jak zachowanie.</span><span class="sxs-lookup"><span data-stu-id="21983-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21983-119">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="21983-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="21983-120">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21983-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="21983-121">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21983-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="21983-122">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21983-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="21983-123">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="21983-123">Demonstrates</span></span>  
 <span data-ttu-id="21983-124">Aby uruchomić przykład, skompiluj projekty klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="21983-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="21983-125">Następnie otwórz dwa okna poleceń i zmień katalogi na \<przykład > \CS\Service\bin\debug i \<przykład > Katalogi \CS\Client\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="21983-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="21983-126">Następnie uruchom usługę, wpisując `service.exe` , a następnie Wywołaj program Client. exe z początkową wartością taktów przekazaną jako argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="21983-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="21983-127">Pokazano przykładowe dane wyjściowe dla 10 taktów.</span><span class="sxs-lookup"><span data-stu-id="21983-127">A sample output for 10 ticks is shown.</span></span>  
  
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
> <span data-ttu-id="21983-128">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="21983-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21983-129">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="21983-129">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="21983-130">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="21983-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21983-131">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="21983-131">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
