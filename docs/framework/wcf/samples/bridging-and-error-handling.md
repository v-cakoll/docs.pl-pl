---
title: Mostkowanie i obsługa błędów
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: 6afaddc75855b7e95ad708b2179cabb9aee35001
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514545"
---
# <a name="bridging-and-error-handling"></a>Mostkowanie i obsługa błędów
Niniejszy przykład pokazuje, jak usługa routingu Windows Communication Foundation (WCF) służy do mostkowanie komunikacji między klientem a usługą, używanego przez różnych powiązania. Ten przykład pokazuje także sposób korzystania z usługi tworzenia kopii zapasowych dla scenariusze trybu failover. Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji. W tym przykładzie dostosowuje się standardowa przykładowe Kalkulator WCF do komunikowania się za pomocą usługi routingu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie klient Kalkulator jest skonfigurowany do wysyłania wiadomości do punktu końcowego uwidocznionego przez router. Usługa routingu jest skonfigurowany do akceptowania wszystkie komunikaty wysyłane do niej i przekazują je do punktu końcowego, który odnosi się do usługi kalkulatora. Następujące punkty opisano w konfiguracji podstawowej usługi Kalkulator, usługę Kalkulator kopii zapasowych i klienta Kalkulator i jak się dzieje komunikacji między klientem a usługą przy użyciu usługi routingu:  
  
-   Klient Kalkulator jest skonfigurowany do użycia BasicHttpBinding, podczas gdy usługa Kalkulator jest skonfigurowana do używania NetTcpBinding. Usługa routingu automatycznie konwertuje komunikaty w razie potrzeby przed wysłaniem ich do usługi Kalkulator i konwertuje ono również odpowiedzi, aby klient Kalkulator mają do nich dostęp.  
  
-   Usługa routingu obsługującemu dwie usługi Kalkulatora: podstawowe usługi Kalkulator i wykonaj kopię zapasową Kalkulator. Usługa routingu najpierw próbuje komunikować się z podstawowego punktu końcowego usługi kalkulatora. Jeśli ta próba kończy się niepowodzeniem ze względu na punkt końcowy jest wciśnięty, usługa routingu próbuje się komunikować z punktem końcowym usługi Kalkulator kopii zapasowych.  
  
 Ten sposób wiadomości wysłanych z klienta są odbierane przez router, a są przekierowane do rzeczywistej usługi kalkulatora. Jeśli punkt końcowy usługi Kalkulator jest wyłączony, usługa routingu kieruje wiadomości z punktem końcowym usługi Kalkulator kopii zapasowych. Komunikaty z Kalkulatora usługi kopii zapasowej są wysyłane do routera usługi, który z kolei przekazuje je do klienta kalkulatora.  
  
> [!NOTE]
>  Wykaz kopii zapasowych może mieć więcej niż jeden punkt końcowy zdefiniowany. W tym przypadku punkt końcowy usługi tworzenia kopii zapasowych nie działa, usługa routingu będzie próbuje nawiązać połączenie do następnego punktu końcowego kopii zapasowych na liście do momentu pomyślnego połączenia wystąpienia.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz RouterBridgingAndErrorHandling.sln.  
  
2.  Naciśnij klawisz F5 lub CTRL + SHIFT + B, w programie Visual Studio  
  
    1.  Jeśli chcesz automatycznie uruchomić projektów konieczne po naciśnięciu klawisza F5, kliknij prawym przyciskiem myszy rozwiązanie, wybierz opcję **właściwości**, a następnie w **projekt startowy** węźle **wspólne właściwości**, wybierz opcję **wiele projektów startowych**, a wszystkie projekty **Start**.  
  
    2.  Jeśli tworzysz projekt za pomocą klawiszy CTRL + SHIFT + B, uruchom następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulator usługi (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu (. / RoutingService/bin/RoutingService.exe)  
  
3.  W kliencie Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta.  
  
     Powinny zostać wyświetlone następujące dane wyjściowe:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera. Możesz również zmienić nazwę pliku App.config się czymś innym, tak aby nie został rozpoznany i usuń znaczniki komentarza wywołania metody, które ma `ConfigureRouterViaCode()`. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 Niniejszy przykład pokazuje routera service pełniący funkcję obsługi mostka i błędów protokołu. W tym scenariuszu routingu opartego na zawartości nie występuje; Usługa routingu działa jako węzeł przezroczystym serwerem proxy skonfigurowane do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych. Usługa routingu wykonuje też dodatkowe kroki w sposób niewidoczny dla użytkownika obsługi błędów występujących podczas próbuje wysyłać do punktów końcowych, że jest skonfigurowany do komunikowania się z. Według działających jako Most protokołu, usługa routingu umożliwia użytkownikowi zdefiniowanie jednego protokołu komunikacji zewnętrznych i inny wpis dla komunikacji wewnętrznej.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce zapewnić punktu końcowego usług międzyoperacyjnych w sieci, przy jednoczesnej optymalizacji wydajności wewnętrznie. Ten sposób uwidacznia jego usług na świecie za pośrednictwem punktu końcowego przy użyciu BasicHttpBinding, używając przy tym wewnętrznie usługa routingu do zestawiania tego połączenia z punktem końcowym za pomocą NetTcpBinding, używane w usługach. Ponadto firma Contoso chce, aby jego oferty być odporne na tymczasowe awarii w jednym z jego produkcji usługi usług, a zatem Wirtualizuje wiele punktów końcowych za zaporą za pomocą usługi routera jego możliwości, aby automatycznie przejściu w tryb failover obsługę błędów Tworzenie kopii zapasowych punktów końcowych, gdy jest to konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
