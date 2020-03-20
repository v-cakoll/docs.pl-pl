---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183636"
---
# <a name="hello-world-with-the-routing-service"></a>Program Hello World z usługą routingu
W tym przykładzie przedstawiono usługę routingu Programu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem WCF, który ułatwia dołączanie routera opartego na zawartości do aplikacji. Ten przykład dostosowuje standardowy przykład kalkulatora WCF do komunikowania się za pomocą usługi routingu. W tym przykładzie klient kalkulatora jest skonfigurowany do wysyłania wiadomości do punktu końcowego udostępnianego przez router. Usługa routingu jest skonfigurowana do akceptowania wszystkich wiadomości wysłanych do niej i przekazywania ich do punktu końcowego odpowiadającego usłudze Kalkulator. W ten sposób wiadomości wysyłane od klienta są odbierane przez router i ponownie kierowane do rzeczywistej usługi Kalkulator. Wiadomości z usługi Kalkulator są wysyłane z powrotem do routera, co z kolei przekazuje je z powrotem do klienta kalkulatora.

### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2012, otwórz HelloRoutingService.sln.

2. Naciśnij klawisze F5 lub CTRL+SHIFT+B.

    > [!NOTE]
    > Po naciśnięciu klawisza F5 klient kalkulatora zostanie automatycznie uruchomiony. Jeśli naciśniesz klawisze CTRL+SHIFT+B (kompilacja), należy rozpocząć obserwowanie aplikacji samodzielnie.
    >
    > 1. Klient kalkulatora (./CalculatorClient/bin/client.exe
    > 2. Usługa kalkulatora (./CalculatorService/bin/service.exe)
    > 3. Usługa routingu (./Usługa routingu/bin/usługa routingu.exe)

3. Naciśnij klawisz ENTER, aby uruchomić klienta.

     Powinny zostać wyświetlone następujące dane wyjściowe:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Konfigurowalne za pomocą kodu lub app.config
 Przykładowe statki skonfigurowane do używania pliku App.config do definiowania zachowania routera. Można również zmienić nazwę pliku App.config na coś innego, tak aby nie został rozpoznany i odkomentować wywołanie metody ConfigureRouterViaCode(). Każda z tych metod powoduje to samo zachowanie z routera.

### <a name="scenario"></a>Scenariusz
 W tym przykładzie pokazano, że router działa jako podstawowa pompa wiadomości. Usługa routingu działa jako przezroczysty węzeł serwera proxy skonfigurowany do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych.

### <a name="real-world-scenario"></a>Scenariusz realny
 Contoso chce zwiększyć elastyczność, która ma w nazewnictwie, adresowaniu, konfiguracji i bezpieczeństwie swoich usług. Aby to zrobić, umieszczają podstawową pompę wiadomości przed swoimi usługami, aby działać jako publiczny punkt końcowy. Dzięki temu można umieścić dodatkowe zabezpieczenia przed ich rzeczywistych usług i ułatwić implementowanie skalowane rozwiązania w poziomie lub wersji usługi w późniejszym terminie.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Zobacz też

- [AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
