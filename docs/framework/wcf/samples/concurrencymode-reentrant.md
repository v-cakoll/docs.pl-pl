---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 2daa802d72a08d31a52a09952d31b718e8a51a90
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816642"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="c2af9-102">Procedura wielobieżna ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="c2af9-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="c2af9-103">Niniejszy przykład pokazuje konieczność i zagadnień dotyczących używania pomocą właściwości ConcurrencyMode.Reentrant od implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c2af9-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="c2af9-104">Pomocą właściwości ConcurrencyMode.Reentrant oznacza, że usługi (lub wywołania zwrotnego) przetwarza tylko jeden komunikat w danym momencie (odpowiednikiem `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="c2af9-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="c2af9-105">Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation (WCF) blokuje `InstanceContext` przetwarzania komunikatu, tak aby nie inne komunikaty mogą być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="c2af9-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="c2af9-106">W przypadku trybu współużytkowane `InstanceContext` jest odblokowany, po prostu, zanim usługa wykonuje wywołanie wychodzące, co pozwoli na kolejne wywołanie, (które mogą być współużytkowane, jak pokazano w przykładzie) można pobrać blokady następnym razem, jest dostępna w usłudze.</span><span class="sxs-lookup"><span data-stu-id="c2af9-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="c2af9-107">Aby zademonstrować zachowanie, przykład pokazuje, jak klienta i usługi mogą wysyłać między sobą za pomocą kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="c2af9-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="c2af9-108">Kontrakt zdefiniowany jest za pomocą kontraktu dwukierunkowego `Ping` metoda implementowanych przez usługę oraz metody wywołania zwrotnego `Pong` implementowanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c2af9-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="c2af9-109">Klient wywołuje serwera `Ping` metody za pomocą znaczników liczba, tym samym inicjowanie wywołania.</span><span class="sxs-lookup"><span data-stu-id="c2af9-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="c2af9-110">Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje wywołania zwrotne `Pong` metody podczas zmniejszanie liczby taktów.</span><span class="sxs-lookup"><span data-stu-id="c2af9-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="c2af9-111">Odbywa się przez następujący kod w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c2af9-111">This is done by the following code in the sample.</span></span>  
  
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
  
 Wywołanie zwrotne `Pong` implementacja ma tę samą logikę jako `Ping` implementacji. Oznacza to, sprawdzi, czy liczba cykli jest różna od zera, a następnie wywołuje `Ping` metody na kanale wywołania zwrotnego (w tym przypadku jest kanału, który został użyty do wysłania, oryginalnym `Ping` wiadomości) przy użyciu znaczników liczba zmniejszona o 1. Gdy tylko liczbę cykli będzie wynosić 0, metoda zwraca wartość w tym samym rozpakowanie wszystkie odpowiedzi powrót do pierwszego wywołania klienta, który zainicjował wywołanie. <span data-ttu-id="c2af9-115">Jest to pokazane w celu wykonania wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c2af9-115">This is shown in the callback implementation.</span></span>  
  
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
  
 Zarówno `Ping` i `Pong` metody to żądanie/nietypizowana odpowiedź, co oznacza, że pierwsze wywołanie `Ping` nie powróci do momentu wywołania `CallbackChannel<T>.Pong()` zwraca. Na komputerze klienckim `Pong` nie może zwracać aż do następnej `Ping` wywołać, aby ustawić jej zwraca. <span data-ttu-id="c2af9-118">Ponieważ zarówno wywołania zwrotnego, jak i usługi muszą połączenia wychodzące żądanie/nietypizowana odpowiedź przed ich potrzebują pomocy eksperta dla oczekującego żądania, zachowanie pomocą właściwości ConcurrencyMode.Reentrant muszą być oznaczone obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="c2af9-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2af9-119">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c2af9-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c2af9-120">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2af9-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c2af9-121">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2af9-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c2af9-122">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2af9-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c2af9-123">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="c2af9-123">Demonstrates</span></span>  
 <span data-ttu-id="c2af9-124">Aby uruchomić przykład, kompilować projekty klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="c2af9-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="c2af9-125">Następnie otwórz dwa okna polecenia i zmień katalogi na \<przykładowe > \CS\Service\bin\debug i \<przykładowe > \CS\Client\bin\debug katalogów.</span><span class="sxs-lookup"><span data-stu-id="c2af9-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="c2af9-126">Następnie uruchom usługę, wpisując `service.exe` i Wywołaj Client.exe wartością początkową taktów przekazywany jako argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="c2af9-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="c2af9-127">Przykładowe dane wyjściowe dla 10 najmniejszych jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="c2af9-127">A sample output for 10 ticks is shown.</span></span>  
  
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
>  <span data-ttu-id="c2af9-128">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c2af9-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2af9-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c2af9-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2af9-130">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c2af9-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2af9-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2af9-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
