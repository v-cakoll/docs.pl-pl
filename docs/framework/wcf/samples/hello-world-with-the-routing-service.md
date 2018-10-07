---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 52b5c3b167cbbfb032d8e6104a118c5c9384938e
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845778"
---
# <a name="hello-world-with-the-routing-service"></a>Program Hello World z usługą routingu
Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji. W tym przykładzie dostosowuje się standardowej próbki Kalkulator WCF do komunikowania się za pomocą usługi routingu. W tym przykładzie klient Kalkulator jest skonfigurowany do wysyłania wiadomości do punktu końcowego uwidocznionego przez router. Usługa routingu jest skonfigurowana do akceptowania wszystkie komunikaty wysyłane do niej i przekazują je do punktu końcowego, który odnosi się do usługi kalkulatora. Ten sposób wiadomości wysłanych z klienta są odebrany przez router i ponownie kierowane do rzeczywistej usługi kalkulatora. Komunikaty z Kalkulatora usługi są wysyłane do routera, który z kolei przekazuje je do klienta kalkulatora.

### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1.  Za pomocą programu Visual Studio 2012, otwórz HelloRoutingService.sln.

2.  Naciśnij klawisz F5 lub CTRL + SHIFT + B.

    > [!NOTE]
    >  Jeśli użytkownik naciśnie klawisz F5, rozpoczyna się automatycznie klienta Kalkulator. Jeśli użytkownik naciśnie klawisz CTRL + SHIFT + B (Kompilacja), należy uruchomić następujące aplikacje samodzielnie.
    >
    > 1.  Kalkulator klienta (./CalculatorClient/bin/client.exe
    > 2.  Kalkulator usługi (. / CalculatorService/bin/service.exe)
    > 3.  Usługa routingu (. / RoutingService/bin/RoutingService.exe)

3.  Naciśnij klawisz ENTER, aby uruchomić klienta.

     Powinny zostać wyświetlone następujące dane wyjściowe:

     Add(100,15.99) = 115.99

     SUBTRACT(145,76.54) = 68.46

     MULTIPLY(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714

## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.Config
 Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera. Można również zmienić nazwę pliku App.config się czymś innym, tak aby nie został rozpoznany i usuń znaczniki komentarza wywołania metody, które ma ConfigureRouterViaCode(). Każda z tych metod powoduje takie samo zachowanie z routera.

### <a name="scenario"></a>Scenariusz
 Niniejszy przykład pokazuje routera będącego pompa podstawowe wiadomości. Usługa routingu działa jako węzeł przezroczystym serwerem proxy skonfigurowane do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych.

### <a name="real-world-scenario"></a>Scenariusz rzeczywistych
 Firma Contoso chce zwiększyć elastyczność, który ma w nazewnictwa, adresowania, konfiguracji i zabezpieczeń swoich usług. Aby to zrobić, mogą umieścić pompy komunikatów podstawowe przed ich usługom, aby pełnić rolę publiczny punkt końcowy umożliwiający dostęp do Internetu. Umożliwi to umieszczenie dodatkową ochronę przed ich rzeczywiste usługi i ułatwić do zaimplementowania Skalowanie rozwiązań lub przechowywanie wersji usługi w późniejszym terminie.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
