---
title: Dynamiczna ponowna konfiguracja
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508210"
---
# <a name="dynamic-reconfiguration"></a>Dynamiczna ponowna konfiguracja
Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji. W tym przykładzie dostosowuje się standardowa przykładowe Kalkulator WCF do komunikowania się za pomocą usługi routingu. Niniejszy przykład pokazuje, jak usługa routingu można dynamicznie tak skonfigurować, podczas wykonywania.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Można dynamicznie zmieniać swoją usługą routingu w czasie wykonywania, w tym przykładzie uruchamia czasomierz co pięć sekund, która tworzy nową <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu i stosuje je. Ta konfiguracja odwołuje się standardowym punktem końcowym kalkulatora lub punkt końcowy Kalkulator zaokrąglania. Aplikacja kliencka Kalkulator ma swoje wiadomości zwrócony z jednej usługi lub innych, w zależności od tego, co jest skonfigurowana usługa routingu w przypadku kierowania do w danym momencie.  
  
 Usługa routingu capabilitiy dla dynamiczna ponowna konfiguracja poprzez niestandardowe zachowanie jest używany. To zachowanie niestandardowe dołącza rozszerzenie usługi, który zawiera proste wątku czasomierz, który jest uruchamiany co pięć sekund, co powoduje wywołanie zwrotne w celu `UpdateRules` metody. To wywołanie zwrotne tworzy i stosuje nową konfigurację routingu. W rzeczywiste wdrożenie to wywołanie zwrotne prawdopodobnie będzie realizowane w wyniku innego typu zdarzenia, takiego jak powiadomienie zdarzenie SQL lub anonsu protokołu WS Discovery.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz DynamicReconfiguration.sln.  
  
2.  Aby otworzyć **Eksploratora rozwiązań**, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.  
  
3.  Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.  
  
    1.  Jeśli chcesz automatycznie uruchomić projektów konieczne po naciśnięciu klawisza **F5**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**. Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie. Wybierz **wiele projektów startowych** przycisk radiowy, a następnie ustaw wszystkie projekty, które mają **Start** akcji.  
  
    2.  Jeśli tworzysz projekt za pomocą **CTRL + SHIFT + B**, należy uruchomić następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulator usługi (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu Kalkulator (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta i wywoływanie operacji usługi kalkulatora.  
  
     Usługa routingu kieruje komunikaty do Kalkulatora zaokrąglania i kalkulatora regularne też jako zmiany konfiguracji routingu dynamicznie co pięć sekund. W zależności od punktu końcowego, które usługa routingu jest skonfigurowana do wysyłania komunikatów do istnieją różne wyniki w oknie konsoli klienta.  
  
5.  Nadal, naciskając klawisz ENTER w więcej niż pięć sekund, a następnie obserwować zmiany w wynikach z usługi.  
  
    1.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli Usługa routera jest skonfigurowana do przesyłania wiadomości w usłudze zaokrąglania Kalkulator.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli usługa routingu jest skonfigurowana do przesyłania wiadomości w usłudze kalkulatora regularne.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Kalkulator usługi i zaokrąglania Kalkulator również wydrukować dziennika operacji wywoływane w celu ich odpowiedniej konsoli systemu windows.  
  
7.  W oknie konsoli klienta wpisz "Zamknij", a następnie naciśnij klawisz ENTER, aby zakończyć.  
  
8.  Naciśnij klawisz ENTER w oknach konsoli usług do zakończenia usługi.  
  
## <a name="scenario"></a>Scenariusz  
 Niniejszy przykład demonstruje routerze działającego jako router opartego na zawartości, dzięki czemu wielu typów lub implementacji usług są dostępne za pośrednictwem punktów końcowych.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce wszystkich swoich usług, aby uwidocznić tylko jeden punkt końcowy publicznie za pomocą którego oferują dostęp do wielu różnych typów usług wirtualizacji. W tym przypadku skorzystają z usługą routingu opartego na zawartości możliwości routingu w celu określenia, gdzie mają być wysyłane żądania przychodzące.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
