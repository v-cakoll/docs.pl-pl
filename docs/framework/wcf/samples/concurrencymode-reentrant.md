---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 67e719afd40b52f37c777cf9791291a16878592f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600091"
---
# <a name="concurrencymode-reentrant"></a>Procedura wielobieżna ConcurrencyMode
Ten przykład pokazuje konieczność i implikacje użycia ConcurrencyMode. using w implementacji usługi. Concurrency. repodmiotu oznacza, że usługa (lub wywołania zwrotne) przetwarza tylko jeden komunikat w danym momencie (analogicznie do `ConcurencyMode.Single` ). Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation (WCF) blokuje `InstanceContext` Przetwarzanie komunikatu, aby nie można było przetworzyć innych komunikatów. W przypadku trybu przechodzenia, `InstanceContext` jest odblokowany tuż przed wykonaniem wywołania wychodzącego przez usługę, co pozwala na kolejne wywołanie (które może być w sposób pokazany w przykładzie), aby uzyskać blokadę po następnym przejściu do usługi. Aby zademonstrować zachowanie, przykład pokazuje, jak klient i usługa mogą wysyłać komunikaty między sobą przy użyciu kontraktu dupleksowego.  
  
 Zdefiniowany kontrakt jest umową dupleksową z `Ping` metodą implementowaną przez usługę i metodę wywołania zwrotnego `Pong` implementowaną przez klienta. Klient wywołuje `Ping` metodę serwera z liczbą cyklów, co spowoduje zainicjowanie wywołania. Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje metodę wywołania zwrotnego `Pong` przy zmniejszeniu liczby taktów. Jest to realizowane przez Poniższy kod w przykładzie.  
  
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
  
 Implementacja wywołania zwrotnego `Pong` ma taką samą logikę jak `Ping` implementacja. Oznacza to, że sprawdza, czy liczba cykli nie jest równa zero, a następnie wywołuje `Ping` metodę w kanale wywołania zwrotnego (w tym przypadku jest to kanał, który został użyty do wysłania oryginalnej `Ping` wiadomości) z liczbą cykli równą 1. Moment, w którym licznik taktu osiągnie wartość 0, metoda zwraca w ten sposób odpakowanie wszystkich odpowiedzi z powrotem do pierwszego wywołania wykonanego przez klienta, który zainicjował wywołanie. Jest to pokazane w implementacji wywołania zwrotnego.  
  
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
  
 Obie `Ping` metody i `Pong` są żądaniami/odpowiedzi, co oznacza, że pierwsze wywołanie `Ping` nie zwraca do momentu wywołania `CallbackChannel<T>.Pong()` zwrotnego. Na kliencie `Pong` Metoda nie może zwrócić do momentu następnego `Ping` wywołania, które wykona. Ponieważ zarówno wywołanie zwrotne, jak i usługa muszą wychodzące wywołania żądania/odpowiedzi, zanim będą mogły odpowiedzieć na oczekujące żądanie, obie implementacje muszą być oznaczone jako takie jak zachowanie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstracje  
 Aby uruchomić przykład, skompiluj projekty klienta i serwera. Następnie otwórz dwa okna poleceń i zmień katalogi na \<sample> katalogi \CS\Service\bin\debug i \<sample> \CS\Client\bin\debug. Następnie uruchom usługę, wpisując `service.exe` , a następnie Wywołaj program Client. exe z początkową wartością taktów przekazaną jako argument wejściowy. Pokazano przykładowe dane wyjściowe dla 10 taktów.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
