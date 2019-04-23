---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 5bee4c7cc2c2e64c6e0d8d0ec2634f9500cd9d51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975874"
---
# <a name="configuration-channel-factory"></a>Fabryka kanałów konfiguracji
Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie Konfiguracja klienta programu WCF. Może to być również przydatne w scenariuszach, w których konfiguracja jest wybrane lub ulegnie zmianie po czas ładowania domeny aplikacji.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Dyskusja
 Ten przykład ilustruje sposób używania <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> można dodać plik konfiguracji określonej aplikacji klienta, bez konieczności używania domyślny plik konfiguracji aplikacji.

 Przykład obejmuje dwa projekty. Pierwszy projekt jest prostą usługę uruchomioną na udzielenie odpowiedzi na komunikaty pochodzące od klientów. Drugi projekt to aplikacja kliencka, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiektów przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> Test.config pliku konfiguracji i są one używane do komunikacji z usługą. Obaj klienci komunikują się z usługą za pomocą konfiguracji określone w Test.config.

 Poniższy kod dodaje plik konfiguracji niestandardowej do aplikacji klienta.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Otwórz program Visual Studio 2012 z uprawnieniami administratora.

2. Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (projekty, 2), a następnie wybierz pozycję **właściwości**.

3. W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.

4. Przenieś **usługi** projektu na początku listy, o **akcji "Start"**, a następnie przenieść **klienta** projektu po **usługi**projektu, również mający **akcji "Start"**, więc **klienta** projektu jest wykonywany po **usługi** projektu.

5. Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5) do uruchomienia przykładu.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
