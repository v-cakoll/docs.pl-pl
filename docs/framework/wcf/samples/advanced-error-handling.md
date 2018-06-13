---
title: Zaawansowana obsługa błędów
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 723b1ca9c2fa771d8bc3f337d9c4fde8c9632c68
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810086"
---
# <a name="advanced-error-handling"></a>Zaawansowana obsługa błędów
W przykładzie pokazano, usługa routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia obejmują routerem na podstawie zawartości w aplikacji. W tym przykładzie pokazano, jak usługa routingu inteligentnie odzyskiwania z błędów przy użyciu transakcji i innych bardziej złożonych pojęć obsługi wiadomości, takie jak multiemisji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie usługi routingu skonfigurowano odczytywać komunikaty z kolejki usługi MSMQ i multiemisji tej wiadomości do dwóch list z kolejki. Jedna lista służy do kolejek usługi service i inny służy do rejestrowania kolejek.  
  
 Ponieważ domyślnie MSMQ powiązanie usługi routingu skonfigurowano Użyj obsługuje transakcje, usługa routingu upewnia się, że wiadomość jest transakcyjna i odebranych przez co najmniej jedna kolejka na wszystkich listach przed zgłoszeniem do (kolejki ruchu przychodzącego `InQ`), że komunikat został pomyślnie skierowany. W związku z tym w przypadku, gdy oba kolejek usługi lub oba kolejek rejestrowania są niedostępne, usługa routingu zgłasza, że nie być kierowane wiadomości i kolejki przychodzącej powinien podjąć inną akcję. Ta akcja składa się z przenoszenie wiadomości do kolejki utraconych wiadomości systemu.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  > [!IMPORTANT]
    >  Zainstaluj usługę MSMQ przed uruchomieniem tego przykładu. Jeśli usługa MSMQ nie jest zainstalowana, zwracany jest komunikat o wyjątku, podczas uruchamiania próbki. Instrukcje dotyczące instalowania usługi MSMQ można znaleźć w folderze [usługi kolejkowania komunikatów instalowanie (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedErrorHandling.sln.  
  
2.  Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.  
  
    1.  W przypadku tworzenia aplikacji z klawiszy CTRL + SHIFT + B, należy uruchomić aplikację w. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  W oknie konsoli naciśnij klawisz ENTER, aby uruchomić klienta.  
  
4.  Różne Statystyka kolejki dla każdego przypadku zwracane przez klienta.  
  
    1.  Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 1 (nie błędów).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 3 (podstawowej usługi i rejestrowania błędów kolejki).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 4 (Rejestrowanie podstawowego i zapasowego kolejki błędy i kolejki głównej usługi).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 2 (niepowodzenie kolejki głównej usługi).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki. Można również zmienić nazwę pliku RoutingService\App.config na inny tak, aby nie został rozpoznany i zmień wartość `configDriven` w RoutingService\Program.cs do `false` do korzystania z konfiguracji zdefiniowane w kodzie. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 W przykładzie pokazano, usługa routingu może obsłużyć zaawansowane możliwości obsługi komunikatów, takie jak transakcji i kontekstu odbierania i czy mogą wykorzystywać te możliwości w ramach poprawnie obsługiwać scenariusze błędu.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Contoso chce korzystać z transakcyjnego odbiera za pośrednictwem usługi routingu, aby upewnić się, że wszystkie niezbędne usługi otrzymywanie informacji, nawet w przypadku błędów. Ponadto chciałby, błędów, które mają być obsługiwane poprawnie i automatycznie i błędów należy podać w przypadku czy wiadomość dostarczona nawet, gdy jest wykorzystywany logiki obsługi błędów. W tym celu skonfigurowano usługę routingu, aby przełączyć się do określonych punktów końcowych, zgodnie z oczekiwaniami i usługa routingu obsługuje sytuacjach błędu w tym tworzenie, uzupełniania i wycofywania/Przerywanie transakcji/odebrać kontekstów jako niezbędne.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
