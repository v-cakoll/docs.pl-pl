---
title: Mostkowanie i obsługa błędów
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: f13a55704422e8a958e55c489f6db11108b03c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bridging-and-error-handling"></a>Mostkowanie i obsługa błędów
W przykładzie pokazano, jak usługa routingu Windows Communication Foundation (WCF) jest używana mostkowania komunikacji między klientem a usługą, która użyć różnych powiązania. W tym przykładzie również przedstawia sposób użycia usługi tworzenia kopii zapasowych dla scenariuszy trybu failover. Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji. W tym przykładzie dostosowuje standardowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbki Kalkulator do komunikowania się przy użyciu usługi routingu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie klient Kalkulator jest skonfigurowany do wysyłania komunikatów do punktu końcowego udostępnianych przez router. Usługa routingu jest skonfigurowany do akceptowania wszystkich wiadomości wysłanych do niego i przekazują je do punktu końcowego, który odpowiada usługi Kalkulator. Następujące punkty opisano konfiguracji podstawowej usługi Kalkulator, usługę Kalkulator kopii zapasowych i klienta Kalkulator i jak komunikacji między klientem a usługą jest wykonywana przy użyciu usługi routingu:  
  
-   Klient Kalkulator jest skonfigurowany do użycia klasy BasicHttpBinding, gdy usługa Kalkulator jest skonfigurowana do używania NetTcpBinding. Usługa routingu automatycznie konwertuje komunikaty w razie potrzeby przed wysłaniem ich do usługi Kalkulator, a także program konwertuje odpowiedzi tak, aby Kalkulator klienta może uzyskiwać do nich dostęp.  
  
-   Usługa routingu zna dwie usługi Kalkulator: głównej usługi Kalkulator i Kalkulator kopii zapasowych. Usługa routingu najpierw próbuje komunikować się z podstawowy punkt końcowy usługi Kalkulator. Jeśli ta próba kończy się niepowodzeniem z powodu punktu końcowego są w dół, usługa routingu następnie próbuje połączyć się z punktem końcowym usługi Kalkulator kopii zapasowych.  
  
 W związku z tym komunikatów wysłanych z klienta są odbierane przez router i są przekierowane do rzeczywistego usługi Kalkulator. Jeśli punkt końcowy usługi Kalkulator działa, usługa routingu kieruje wiadomości z punktem końcowym usługi Kalkulator kopii zapasowych. Komunikaty z usługi Kalkulator kopie zapasowe są odsyłane do routera usługi, który z kolei przekazuje je do Kalkulatora klienta.  
  
> [!NOTE]
>  Listę kopii zapasowych może mieć więcej niż jeden punkt końcowy zdefiniowany. W tym przypadku jeśli punkt końcowy usługi tworzenia kopii zapasowych jest wyłączony, usługa routingu próbuje połączyć się następnego punktu końcowego kopii zapasowych na liście, dopóki nie wystąpi w przypadku pomyślnego nawiązania połączenia.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz RouterBridgingAndErrorHandling.sln.  
  
2.  Naciśnij klawisz F5 lub CTRL + SHIFT + B w programie Visual Studio  
  
    1.  Jeśli chcesz automatyczne uruchamianie niezbędne projektów po naciśnięciu klawisza F5, kliknij prawym przyciskiem myszy rozwiązanie, wybierz **właściwości**i w **projekt startowy** węźle **wspólne właściwości**, wybierz pozycję **wiele projektów startowych**i ustaw wszystkie projekty **Start**.  
  
    2.  W przypadku tworzenia projektu z klawiszy CTRL + SHIFT + B, uruchom następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Usługa kalkulatora (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu (. / RoutingService/bin/RoutingService.exe)  
  
3.  W kliencie programu Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta.  
  
     Powinny być widoczne następujące dane wyjściowe:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki. Można również zmienić nazwę pliku App.config do innego elementu tak, aby nie został rozpoznany i Usuń komentarz wywołanie metody `ConfigureRouterViaCode()`. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 W przykładzie pokazano router usługi działający jako mostka i błąd obsługi protokołu. W tym scenariuszu routingu na podstawie zawartości nie występuje; Usługa routingu działa jako węzeł przezroczystego obiektu pośredniczącego skonfigurowane do przekazywania wiadomości bezpośrednio do zbioru wstępnie skonfigurowane miejsce docelowe punktów końcowych. Usługa routingu wykonuje również dodatkowe kroki w przezroczysty sposób obsługi błędów występujących podczas próby do wysyłania do punktów końcowych, że jest skonfigurowana do komunikacji z. Działając jako mostka protokołu, usługa routingu umożliwia użytkownikowi zdefiniowanie jeden protokół komunikacji zewnętrznej i drugi dla wewnętrznej komunikacji.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce dostarczyć punkt końcowy usługi interoperacyjne w sieci, podczas optymalizacji wydajności wewnętrznie. W związku z tym eksponuje jego usług na świecie za pośrednictwem punktu końcowego za pomocą klasy BasicHttpBinding, podczas wewnętrznie przy użyciu usługi routingu do zestawiania tego połączenia z punktem końcowym przy użyciu NetTcpBinding, którego użyć swoich usług. Ponadto firma Contoso chce jego oferty być odporny na błędy tymczasowych przestojów w jednym z ich produkcji usługi usług i w związku z tym Wirtualizuje wiele punktów końcowych za router z usługi do obsługi błędu funkcji automatycznie w tryb failover Tworzenie kopii zapasowych punktów końcowych, gdy jest to konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
