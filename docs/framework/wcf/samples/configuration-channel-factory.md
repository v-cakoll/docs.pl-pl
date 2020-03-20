---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183947"
---
# <a name="configuration-channel-factory"></a>Fabryka kanałów konfiguracji
Ten przykład obejmuje użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. Umożliwia <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> centralne zarządzanie konfiguracją klienta WCF. Może to być również przydatne w scenariuszach, w których konfiguracja jest zaznaczona lub zmieniona po czasie ładowania domeny aplikacji.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Dyskusji
 W tym przykładzie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pokazano, jak użyć do dodania określonego pliku konfiguracyjnego do aplikacji klienckiej, bez konieczności używania domyślnego pliku konfiguracji aplikacji.

 Próba składa się z dwóch projektów. Pierwszy projekt jest prostą usługą, która działa, aby odpowiedzieć na wiadomości pochodzące od klientów. Drugi projekt jest aplikacją kliencką, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiekty przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> pliku konfiguracji Test.config i używa ich do komunikowania się z usługą. Obaj klienci komunikują się z usługą przy użyciu konfiguracji określonej w Test.config.

 Poniższy kod dodaje niestandardowy plik konfiguracji do aplikacji klienckiej.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Otwórz program Visual Studio 2012 z uprawnieniami administratora.

2. Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (2 projekty), a następnie wybierz polecenie **Właściwości**.

3. W **obszarze Właściwości wspólne**wybierz pozycję Projekt **uruchomienia**, a następnie kliknij pozycję Wiele **projektów startowych**.

4. Przenieś projekt **usługi** na początek listy, z **akcji "Start",** a następnie przenieść projekt **klienta** po projekcie **usługi,** również z **akcji "Start",** więc projekt **klienta** jest wykonywany po projekt **usługi.**

5. Kliknij **przycisk OK**, a następnie naciśnij klawiszE F5 (lub CTRL+F5), aby uruchomić próbkę.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
