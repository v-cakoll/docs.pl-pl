---
title: Procedura wielobieżna ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: c5fa690ca3b8ffe14eb9f19f0bb096b867ab992f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533454"
---
# <a name="concurrencymode-reentrant"></a>Procedura wielobieżna ConcurrencyMode
Niniejszy przykład pokazuje konieczność i zagadnień dotyczących używania pomocą właściwości ConcurrencyMode.Reentrant od implementacji usługi. Pomocą właściwości ConcurrencyMode.Reentrant oznacza, że usługi (lub wywołania zwrotnego) przetwarza tylko jeden komunikat w danym momencie (odpowiednikiem `ConcurencyMode.Single`). Aby zapewnić bezpieczeństwo wątków, Windows Communication Foundation (WCF) blokuje `InstanceContext` przetwarzania komunikatu, tak aby nie inne komunikaty mogą być przetwarzane. W przypadku trybu współużytkowane `InstanceContext` jest odblokowany, po prostu, zanim usługa wykonuje wywołanie wychodzące, co pozwoli na kolejne wywołanie, (które mogą być współużytkowane, jak pokazano w przykładzie) można pobrać blokady następnym razem, jest dostępna w usłudze. Aby zademonstrować zachowanie, przykład pokazuje, jak klienta i usługi mogą wysyłać między sobą za pomocą kontraktu dwukierunkowego.  
  
 Kontrakt zdefiniowany jest za pomocą kontraktu dwukierunkowego `Ping` metoda implementowanych przez usługę oraz metody wywołania zwrotnego `Pong` implementowanych przez klienta. Klient wywołuje serwera `Ping` metody za pomocą znaczników liczba, tym samym inicjowanie wywołania. Usługa sprawdza, czy liczba cykli nie jest równa 0, a następnie wywołuje wywołania zwrotne `Pong` metody podczas zmniejszanie liczby taktów. Odbywa się przez następujący kod w przykładzie.  
  
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
  
 Wywołanie zwrotne `Pong` implementacja ma tę samą logikę jako `Ping` implementacji. Oznacza to, sprawdzi, czy liczba cykli jest różna od zera, a następnie wywołuje `Ping` metody na kanale wywołania zwrotnego (w tym przypadku jest kanału, który został użyty do wysłania, oryginalnym `Ping` wiadomości) przy użyciu znaczników liczba zmniejszona o 1. Gdy tylko liczbę cykli będzie wynosić 0, metoda zwraca wartość w tym samym rozpakowanie wszystkie odpowiedzi powrót do pierwszego wywołania klienta, który zainicjował wywołanie. Jest to pokazane w celu wykonania wywołania zwrotnego.  
  
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
  
 Zarówno `Ping` i `Pong` metody to żądanie/nietypizowana odpowiedź, co oznacza, że pierwsze wywołanie `Ping` nie powróci do momentu wywołania `CallbackChannel<T>.Pong()` zwraca. Na komputerze klienckim `Pong` nie może zwracać aż do następnej `Ping` wywołać, aby ustawić jej zwraca. Ponieważ zarówno wywołania zwrotnego, jak i usługi muszą połączenia wychodzące żądanie/nietypizowana odpowiedź przed ich potrzebują pomocy eksperta dla oczekującego żądania, zachowanie pomocą właściwości ConcurrencyMode.Reentrant muszą być oznaczone obu implementacjach.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="demonstrates"></a>Demonstracje  
 Aby uruchomić przykład, kompilować projekty klienta i serwera. Następnie otwórz dwa okna polecenia i zmień katalogi na \<przykładowe > \CS\Service\bin\debug i \<przykładowe > \CS\Client\bin\debug katalogów. Następnie uruchom usługę, wpisując `service.exe` i Wywołaj Client.exe wartością początkową taktów przekazywany jako argument wejściowy. Przykładowe dane wyjściowe dla 10 najmniejszych jest wyświetlany.  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## <a name="see-also"></a>Zobacz też
