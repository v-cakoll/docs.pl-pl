---
title: Dynamiczna ponowna konfiguracja
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: 81a2b494c48476e683053e12e58264e756201124
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810383"
---
# <a name="dynamic-reconfiguration"></a>Dynamiczna ponowna konfiguracja
W przykładzie pokazano, usługa routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia obejmują routerem na podstawie zawartości w aplikacji. W tym przykładzie dostosowuje próbki Kalkulator WCF wzorcowej do komunikowania się przy użyciu usługi routingu. W tym przykładzie pokazano, jak usługa routingu można dynamicznie tak skonfigurować, w czasie wykonywania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Można dynamicznie zmieniać swoją usługę routingu w czasie wykonywania, w tym przykładzie generowane czasomierza co pięć sekund, która tworzy nowy <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu i stosuje je. Ta konfiguracja odwołuje się do regularnych punktu końcowego Kalkulator lub punkt końcowy Kalkulator zaokrąglania. Aplikacja kliencka Kalkulator ma jego komunikaty zwracane z jednej usługi lub inne, w zależności od tego, które z nich usługi routingu skonfigurowano do trasy, w tym czasie.  
  
 Usługa routingu capabilitiy dynamicznej zmiany konfiguracji przy użyciu niestandardowych zachowanie jest używany. To zachowanie niestandardowych dołącza rozszerzenie usługi zawiera proste wątku czasomierza generowane co pięć sekund, co powoduje wywołanie zwrotne do `UpdateRules` metody. To wywołanie zwrotne tworzy i stosuje nową konfigurację routingu. We wdrożeniu rzeczywiste tego wywołania zwrotnego prawdopodobnie będzie wykonywać wyniku innego typu zdarzeń, takich jak powiadomienia zdarzenie SQL lub anonsu protokołu WS-Discovery.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz DynamicReconfiguration.sln.  
  
2.  Aby otworzyć **Eksploratora rozwiązań**, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.  
  
3.  Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.  
  
    1.  Jeśli chcesz automatyczne uruchamianie niezbędne projektów po naciśnięciu **F5**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**. Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie. Wybierz **wiele projektów startowych** przycisk radiowy i ustaw wszystkie projekty, które mają **Start** akcji.  
  
    2.  W przypadku tworzenia projektu z **CTRL + SHIFT + B**, należy uruchomić następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Usługa kalkulatora (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu kalkulatora (. / RoundingCalcService/bin/service.exe)  
  
        4.  Obiektu RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta i wywoływanie operacji usługi Kalkulator.  
  
     Usługa routingu kieruje komunikaty do Kalkulatora zaokrąglania i regularnego Kalkulator również jako routingu zmiany konfiguracji dynamicznie co pięć sekund. W zależności od tego, który punkt końcowy, usługa routingu jest skonfigurowany do wysyłania komunikatów do istnieją różne wyniki w oknie konsoli klienta.  
  
5.  Kontynuuj, naciskając klawisz ENTER w więcej niż pięciu sekund i Sprawdź zmiany wyników z usługi.  
  
    1.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli Usługa routera jest skonfigurowana do przesyłania wiadomości z usługą Kalkulator zaokrąglania.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli skonfigurowano usługę routingu do wyznaczania tras wiadomościom regularne usługi Kalkulator.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Kalkulator usługi oraz zaokrąglania Kalkulator również wydrukować dziennik operacji wywoływane w celu ich odpowiednich konsoli systemu windows.  
  
7.  W oknie konsoli klienta wpisz "Zamknij", a następnie naciśnij klawisz ENTER, aby zakończyć.  
  
8.  Naciśnij klawisz ENTER w oknach konsoli usług zakończenie usług.  
  
## <a name="scenario"></a>Scenariusz  
 W tym przykładzie przedstawiono router działająca jako router na podstawie zawartości stosowanie wielu typów lub implementacji usług są dostępne za pośrednictwem jeden punkt końcowy.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce wszystkie ich usługi do udostępnienia tylko jeden punkt końcowy publicznie za pośrednictwem której zapewniają dostęp do wielu różnych typów usług wirtualizacji. W takim przypadku wykorzystania usługi routingu na podstawie zawartości możliwości routingu ustalenie wysyłania żądań przychodzących.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
