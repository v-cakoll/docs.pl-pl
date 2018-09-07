---
title: Zaawansowana obsługa błędów
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084146"
---
# <a name="advanced-error-handling"></a>Zaawansowana obsługa błędów
Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji. Niniejszy przykład pokazuje, jak usługa routingu inteligentnie odzyskiwania sprawności błędów, za pomocą transakcji i inne bardziej złożonych koncepcji obsługi komunikatów, takich jak multiemisji.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie usługa routingu skonfigurowano odczytywać komunikaty z kolejki usługi MSMQ i multiemisji ten komunikat do list dwóch kolejek. Jedną listę służy do kolejek usługi service i inny jest używana do rejestrowania kolejek.  
  
 Ponieważ domyślnie powiązanie usługi MSMQ usługa routingu jest skonfigurowany do użycia obsługuje transakcje, usługa routingu sprawia, że się, że wiadomości transakcyjne i odebranych przez co najmniej jedną kolejką na wszystkich listach przed zgłoszeniem do (kolejki dla ruchu przychodzącego `InQ`) który komunikat został pomyślnie kierowany. W związku z tym w przypadku, gdy obie z kolejek usługi i / lub kolejek rejestrowania są niedostępne, usługa routingu zgłasza, że komunikat nie może być kierowany i kolejki elementów przychodzących powinno zająć określonej akcji. Ta akcja składa się z przenoszenie wiadomości do kolejki utraconych wiadomości systemu.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  > [!IMPORTANT]
    >  Przed uruchomieniem tego przykładu, należy zainstalować usługi MSMQ. Jeśli usługa MSMQ nie jest zainstalowany, zwracany jest komunikat o wyjątku, podczas uruchamiania przykładu. Instrukcje dotyczące instalowania usługi MSMQ znajduje się w temacie [instalowanie komunikatów usługi kolejkowania wiadomości (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedErrorHandling.sln.  
  
2.  Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.  
  
    1.  Jeśli tworzysz aplikację za pomocą klawiszy CTRL + SHIFT + B, należy uruchomić tę aplikację u. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  W oknie konsoli naciśnij klawisz ENTER, aby uruchomić klienta.  
  
4.  Różne statystyki dotyczące kolejki w każdym przypadku zwracane przez klienta.  
  
    1.  Poniżej znajduje się dane wyjściowe zwracane w przypadku 1 (Brak błędów).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Poniżej znajduje się dane wyjściowe zwracane w przypadku 3 (podstawowej usługi i rejestrowania błędów kolejki).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Poniżej znajduje się dane wyjściowe zwracane w przypadku 4 (podstawowa usługa kolejki i rejestrowanie podstawowych i zapasowych kolejki błędów).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Poniżej znajduje się dane wyjściowe zwracane w przypadku 2 (niepowodzenie kolejki głównej usługi).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera. Możesz również zmienić nazwę pliku RoutingService\App.config się czymś innym, tak, aby nie został rozpoznany i zmień wartość właściwości `configDriven` pole RoutingService\Program.cs do `false` do korzystania z konfiguracji zdefiniowana w kodzie. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 Niniejszy przykład pokazuje, że usługa routingu mogą obsługiwać zaawansowane funkcje obsługi komunikatów, takie jak transakcje i odbierania kontekstu i użyć tych funkcji w ramach poprawnie Obsługa scenariuszy błąd.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Contoso chce korzystać transakcyjnych odbiera za pośrednictwem usługi routingu, aby upewnić się, że wszystkie niezbędne usługi otrzymywanie informacji, nawet w trakcie warunków błędów. Ponadto chciałby, błędy, które mają być obsługiwane poprawnie i automatycznie i błędów, należy podać w przypadku, że komunikat nie można dostarczyć nawet wtedy, gdy logika obsługi błędów jest wykorzystywany. W tym celu skonfigurowana usługa routingu do trybu failover do określonych punktów końcowych, zgodnie z oczekiwaniami, a usługa routingu obsługuje sytuacje, w tym tworzenie, uzupełnianie i wycofania/Przerywanie transakcji i odbierania kontekstów jako wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
