---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 0ac3b811c59abfbb3148ddad3d518443f7633adc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714966"
---
# <a name="concurrencymode-reentrant"></a>Procedura wielobieżna ConcurrencyMode
Ten przykład pokazuje konieczność i implikacje użycia ConcurrencyMode. using w implementacji usługi. Concurrency. repodmiotu oznacza, że usługa (lub wywołanie zwrotne) przetwarza tylko jeden komunikat w danym momencie (analogiczny do `ConcurencyMode.Single`). Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation (WCF) blokuje `InstanceContext` przetwarzania wiadomości, dzięki czemu nie można przetwarzać innych komunikatów. W przypadku trybu remarketingowego `InstanceContext` jest odblokowana tuż przed wykonaniem wywołania wychodzącego, co pozwala na kolejne wywołanie (które może być źródłem, jak pokazano w przykładzie), aby uzyskać blokadę po następnym przejściu do usługi. Aby zademonstrować zachowanie, przykład pokazuje, jak klient i usługa mogą wysyłać komunikaty między sobą przy użyciu kontraktu dupleksowego.  
  
 Zdefiniowany kontrakt jest umową dwukierunkową z metodą `Ping` implementowaną przez usługę i metodę wywołania zwrotnego `Pong` implementowaną przez klienta. Klient wywołuje metodę `Ping` serwera z liczbą cyklów, co spowoduje zainicjowanie wywołania. Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje wywołania zwrotne `Pong` metody przy zmniejszeniu liczby taktów. Jest to realizowane przez Poniższy kod w przykładzie.  
  
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
  
 Implementacja `Pong` wywołania zwrotnego ma taką samą logikę jak implementacja `Ping`. Oznacza to, że sprawdza, czy liczba cykli nie jest równa zero, a następnie wywołuje metodę `Ping` w kanale wywołania zwrotnego (w tym przypadku jest to kanał, który został użyty do wysłania oryginalnego komunikatu `Ping`) z liczbą cykli równą 1. Moment, w którym licznik taktu osiągnie wartość 0, metoda zwraca w ten sposób odpakowanie wszystkich odpowiedzi z powrotem do pierwszego wywołania wykonanego przez klienta, który zainicjował wywołanie. Jest to pokazane w implementacji wywołania zwrotnego.  
  
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
  
 Zarówno `Ping`, jak i `Pong` są żądania/odpowiedzi, co oznacza, że pierwsze wywołanie `Ping` nie zwraca do momentu zwrócenia wywołania do `CallbackChannel<T>.Pong()`. Na kliencie Metoda `Pong` nie może zostać zwrócona do momentu następnego wywołania `Ping`, które nastąpi. Ponieważ zarówno wywołanie zwrotne, jak i usługa muszą wychodzące wywołania żądania/odpowiedzi, zanim będą mogły odpowiedzieć na oczekujące żądanie, obie implementacje muszą być oznaczone jako takie jak zachowanie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Przedstawia  
 Aby uruchomić przykład, skompiluj projekty klienta i serwera. Następnie otwórz dwa okna poleceń i zmień katalogi na \<przykład > \CS\Service\bin\debug i \<przykład > Katalogi \CS\Client\bin\debug. Następnie uruchom usługę, wpisując `service.exe`, a następnie Wywołaj program Client. exe z początkową wartością taktów przekazaną jako argument wejściowy. Pokazano przykładowe dane wyjściowe dla 10 taktów.  
  
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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
