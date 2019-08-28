---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045655"
---
# <a name="configuration-channel-factory"></a>Fabryka kanałów konfiguracji
Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie konfiguracją klienta programu WCF. Może to być również przydatne w scenariuszach, w których konfiguracja jest wybierana lub zmieniana po upływie czasu ładowania domeny aplikacji.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Dyskusji
 Ten przykład pokazuje, jak używać <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> do dodawania określonego pliku konfiguracji do aplikacji klienckiej bez konieczności używania domyślnego pliku konfiguracji aplikacji.

 Przykład składa się z dwóch projektów. Pierwszy projekt to prosta usługa, która jest uruchamiana w celu odpowiedzi na komunikaty pochodzące z klientów. Drugi projekt jest aplikacją kliencką, która kompiluje <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> dwa obiekty <xref:System.Configuration.ExeConfigurationFileMap> przy użyciu dla pliku konfiguracji test. config i używa ich do komunikowania się z usługą. Obaj klienci komunikują się z usługą przy użyciu konfiguracji określonej w pliku test. config.

 Poniższy kod dodaje niestandardowy plik konfiguracji do aplikacji klienckiej.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Otwórz program Visual Studio 2012 z uprawnieniami administratora.

2. Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (2 projekty), a następnie wybierz polecenie **Właściwości**.

3. W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie kliknij pozycję **wiele projektów startowych**.

4. Przenieś projekt **usługi** na początek listy, z **akcją "Start"** , a następnie przenieś projekt **klienta** po projekcie **usługi** , również z **akcją "Start"** , tak aby projekt **klienta** był wykonywany po projekcie **usługi** .

5. Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5), aby uruchomić przykład.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
