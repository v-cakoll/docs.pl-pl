---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: d0ecd4b0c39c6a736a176a61490f454c2bab2e20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502647"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="caadb-102">Procedura wielobieżna ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="caadb-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="caadb-103">W przykładzie pokazano konieczność i zagadnień dotyczących używania pomocą właściwości ConcurrencyMode.Reentrant implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="caadb-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="caadb-104">Pomocą właściwości ConcurrencyMode.Reentrant oznacza, że usługa (lub wywołania zwrotnego) przetwarza tylko jeden komunikat w danym momencie (odpowiednikiem `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="caadb-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="caadb-105">Aby zapewnić bezpieczeństwo wątków, blokuje Windows Communication Foundation (WCF) `InstanceContext` przetwarza komunikat, że nie inne komunikaty mogą być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="caadb-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="caadb-106">W przypadku trybu współużytkowane `InstanceContext` jest odblokowany, tuż przed usługa wykonuje wywołanie wychodzące, umożliwiając kolejne wywołania (która może być współużytkowane, jak pokazano w przykładzie) można uzyskać blokady następnym pochodzi z usługą.</span><span class="sxs-lookup"><span data-stu-id="caadb-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="caadb-107">Aby zademonstrować zachowanie, próbki pokazuje, jak klient i usługa może wysyłać wiadomości między sobą za pomocą kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="caadb-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="caadb-108">Kontrakt zdefiniowany jest kontrakt dupleksu `Ping` Metoda implementowana przez usługę i metodę wywołania zwrotnego `Pong` implementowana przez klienta.</span><span class="sxs-lookup"><span data-stu-id="caadb-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="caadb-109">Klient wywołuje serwera `Ping` metody za pomocą znaczników liczba, tym samym inicjowanie wywołanie.</span><span class="sxs-lookup"><span data-stu-id="caadb-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="caadb-110">Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje wywołania zwrotne `Pong` metoda podczas zmniejszanie liczby znaczników.</span><span class="sxs-lookup"><span data-stu-id="caadb-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="caadb-111">Jest to realizowane przez następujący kod w próbce.</span><span class="sxs-lookup"><span data-stu-id="caadb-111">This is done by the following code in the sample.</span></span>  
  
```  
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
  
 Wywołanie zwrotne `Pong` implementacji ma tej samej logiki, `Ping` implementacji. Oznacza to, sprawdza, czy liczba cykli nie jest równa zero, a następnie wywołuje `Ping` metody w kanale wywołania zwrotnego (w tym przypadku jest kanału, który został użyty do wysłania oryginalnej `Ping` wiadomości) o znaczników liczba zmniejszany przez 1. Liczba cykli wynosić 0, metoda zwraca co momentu odkodowywania wszystkie odpowiedzi do pierwsze wywołanie przez klienta, który zainicjował rozmowę telefoniczną. <span data-ttu-id="caadb-115">Przedstawiono to w celu wykonania wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="caadb-115">This is shown in the callback implementation.</span></span>  
  
```  
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
  
 Zarówno `Ping` i `Pong` metody są żądania/odpowiedzi, co oznacza, że w pierwszym wywołaniu `Ping` nie powróci do wywołania `CallbackChannel<T>.Pong()` zwraca. Na komputerze klienckim `Pong` nie może zwracać aż do następnego `Ping` wywołanie, że on zwraca. <span data-ttu-id="caadb-118">Ponieważ zarówno wywołania zwrotnego, jak i usługi musi być wychodzące żądania/odpowiedzi przed ich odpowiedzieć oczekujące żądania, zachowanie pomocą właściwości ConcurrencyMode.Reentrant muszą być oznaczone zarówno implementacji.</span><span class="sxs-lookup"><span data-stu-id="caadb-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="caadb-119">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="caadb-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="caadb-120">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="caadb-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="caadb-121">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="caadb-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="caadb-122">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="caadb-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="caadb-123">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="caadb-123">Demonstrates</span></span>  
 <span data-ttu-id="caadb-124">Aby uruchomić przykład, kompilacji projektów klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="caadb-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="caadb-125">Następnie otwórz dwa okna polecenia i przejdź do \<próbki > \CS\Service\bin\debug i \<próbki > \CS\Client\bin\debug katalogów.</span><span class="sxs-lookup"><span data-stu-id="caadb-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="caadb-126">Następnie uruchom usługę, wpisując `service.exe` , a następnie wywołać Client.exe o początkowej wartości Takty przekazany jako argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="caadb-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="caadb-127">Przedstawiono przykładowe dane wyjściowe do 10 znaczniki osi.</span><span class="sxs-lookup"><span data-stu-id="caadb-127">A sample output for 10 ticks is shown.</span></span>  
  
```  
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
>  <span data-ttu-id="caadb-128">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="caadb-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="caadb-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="caadb-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="caadb-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="caadb-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="caadb-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="caadb-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a><span data-ttu-id="caadb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caadb-132">See Also</span></span>
