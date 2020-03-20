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
# <a name="concurrencymode-reentrant"></a>Procedura wielobieżna ConcurrencyMode
W tym przykładzie pokazano konieczność i implikacje przy użyciu ConcurrencyMode.Reentrant w implementacji usługi. WspółbieżnośćMode.Reentrant oznacza, że usługa (lub wywołanie zwrotne) przetwarza tylko jedną `ConcurencyMode.Single`wiadomość w danym czasie (analogiczne do ). Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation `InstanceContext` (WCF) blokuje przetwarzanie wiadomości, dzięki czemu nie można przetwarzać żadnych innych wiadomości. W przypadku trybu `InstanceContext` reentrant, jest odblokowany tuż przed usługa wykonuje połączenie wychodzące, umożliwiając w ten sposób kolejne wywołanie (które mogą być ponownie przedstawione, jak pokazano w próbce), aby uzyskać blokadę następnym razem, gdy przychodzi do usługi. Aby zademonstrować zachowanie, w przykładzie pokazano, jak klient i usługa może wysyłać wiadomości między sobą przy użyciu umowy dupleksu.  
  
 Zdefiniowana umowa jest kontraktem `Ping` dupleksowym z metodą implementowana `Pong` przez usługę i metodą wywołania zwrotnego implementowana przez klienta. Klient wywołuje `Ping` metodę serwera z liczbą znaczników, inicjując w ten sposób wywołanie. Usługa sprawdza, czy liczba znaczników nie jest równa 0, `Pong` a następnie wywołuje metodę wywołań zwrotnych podczas zmniejszania liczby znaczników. Odbywa się to za pomocą następującego kodu w przykładzie.  
  
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
  
 Implementacja wywołania `Pong` zwrotnego ma taką `Ping` samą logikę jak implementacja. Oznacza to, że sprawdza, czy liczba znaczników `Ping` nie jest równa zero, a następnie wywołuje metodę na kanale wywołania zwrotnego (w tym przypadku jest to kanał, który został użyty do wysłania oryginalnej `Ping` wiadomości) z liczbą znaczników zmniejszanych o 1. W momencie, gdy liczba znaczników osiągnie 0, metoda zwraca w ten sposób rozpakowywanie wszystkich odpowiedzi z powrotem do pierwszego wywołania wykonanego przez klienta, który zainicjował wywołanie. Jest to pokazane w implementacji wywołania zwrotnego.  
  
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
  
 Zarówno `Ping` i `Pong` metody są żądanie/odpowiedź, co oznacza, że pierwsze wywołanie `Ping` nie zwraca, dopóki wywołanie `CallbackChannel<T>.Pong()` zwraca. Na kliencie `Pong` metoda nie może `Ping` powrócić do następnego wywołania, które zostało wykonane zwraca. Ponieważ zarówno wywołania zwrotnego, jak i usługi musi nawiązać wychodzące wywołania żądania/odpowiedzi, zanim będą mogli odpowiedzieć na oczekujące żądanie, obie implementacje muszą być oznaczone zachowaniem ConcurrencyMode.Reentrant.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstracje  
 Aby uruchomić przykład, skompiluj projekty klienta i serwera. Następnie otwórz dwa okna poleceń i \<zmień katalogi na przykładowe>\CS\Service\bin\debug i \<próbkowanie katalogów>\CS\Client\bin\debug. Następnie uruchom usługę, `service.exe` wpisując, a następnie wywołaj client.exe z początkową wartością znaczników przekazanych jako argument wejściowy. Pokazano przykładowe dane wyjściowe dla 10 znaczników.  
  
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
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
