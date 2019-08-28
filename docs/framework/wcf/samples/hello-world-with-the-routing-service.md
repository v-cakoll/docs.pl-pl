---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 1ab3da97bc94f864bbd28ca072f4df8f7d854ea1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044938"
---
# <a name="hello-world-with-the-routing-service"></a>Program Hello World z usługą routingu
Ten przykład pokazuje usługę routingu Windows Communication Foundation (WCF). Usługa routingu to składnik WCF, który ułatwia dołączanie routera opartego na zawartości w aplikacji. Ten przykład dostosowuje standardowy przykład kalkulatora WCF do komunikowania się przy użyciu usługi routingu. W tym przykładzie klient kalkulatora jest skonfigurowany do wysyłania komunikatów do punktu końcowego uwidocznionego przez router. Usługa routingu jest skonfigurowana do akceptowania wszystkich wysyłanych do nich komunikatów i przekazywania ich do punktu końcowego, który odpowiada usłudze Kalkulator. W ten sposób komunikaty wysyłane z klienta są odbierane przez router i ponownie kierowane do rzeczywistej usługi kalkulatora. Komunikaty z usługi kalkulatora są odsyłane do routera, co z kolei przekazuje je do klienta kalkulatora.

### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012 Otwórz HelloRoutingService. sln.

2. Naciśnij klawisz F5 lub CTRL + SHIFT + B.

    > [!NOTE]
    > Po naciśnięciu klawisza F5 klient kalkulatora zostanie automatycznie uruchomiony. Jeśli naciśniesz klawisze CTRL + SHIFT + B (kompilacja), musisz samodzielnie uruchomić następujące aplikacje.
    >
    > 1. Klient kalkulatora (./CalculatorClient/bin/client.exe
    > 2. Usługa kalkulatora (./CalculatorService/bin/service.exe)
    > 3. Usługa routingu (./RoutingService/bin/RoutingService.exe)

3. Naciśnij klawisz ENTER, aby uruchomić klienta.

     Powinny zostać wyświetlone następujące dane wyjściowe:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Konfigurowalne za pośrednictwem kodu lub pliku App. config
 Przykładowe statki skonfigurowane do korzystania z pliku App. config w celu zdefiniowania zachowania routera. Możesz również zmienić nazwę pliku App. config na inną, tak aby nie została rozpoznana, i usunąć komentarz wywołania metody do ConfigureRouterViaCode (). Każda metoda powoduje takie samo zachowanie z routera.

### <a name="scenario"></a>Scenariusz
 Ten przykład pokazuje router działający jako podstawowa pompa komunikatów. Usługa routingu działa jako przezroczysty węzeł serwera proxy skonfigurowany do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych.

### <a name="real-world-scenario"></a>Real World — scenariusz
 Firma Contoso chce zwiększyć elastyczność w zakresie nazewnictwa, określania adresów, konfiguracji i bezpieczeństwa usług. W tym celu należy umieścić podstawową pompę komunikatów przed swoimi usługami, aby działała jako publiczny punkt końcowy. Dzięki temu można umieścić dodatkowe zabezpieczenia przed rzeczywistymi usługami i ułatwić wdrożenie skalowalnych rozwiązań lub przechowywanie wersji usług w późniejszym czasie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
