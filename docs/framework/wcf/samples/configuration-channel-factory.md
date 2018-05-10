---
title: Fabryka kanałów konfiguracji
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: fc3a564128e520133c2404a82438e692b1381875
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-channel-factory"></a>Fabryka kanałów konfiguracji
W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie konfiguracją klienta WCF. Może to być również przydatne w scenariuszach, w których konfiguracja jest wybrane lub zmienić po czas ładowania domeny aplikacji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład przedstawia sposób użycia <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> można dodać pliku określoną konfigurację do aplikacji klienckiej, bez konieczności używania domyślny plik konfiguracji aplikacji.  
  
 Przykład zawiera dwa projekty. Pierwszy projekt jest proste usługa, która działa na udzielenie odpowiedzi na wiadomości przychodzących od klientów. Drugi projekt jest aplikacji klienckiej, która tworzy dwa <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> obiektów przy użyciu <xref:System.Configuration.ExeConfigurationFileMap> Test.config pliku konfiguracji i używa ich do komunikowania się z usługą. Obaj klienci komunikują się z usługą za pomocą konfiguracji określone w Test.config.  
  
 Poniższy kod dodaje plik konfiguracji niestandardowej do aplikacji klienckiej.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] z uprawnieniami administratora.  
  
2.  Kliknij prawym przyciskiem myszy rozwiązanie ConfigurationChannelFactory (projekty 2), a następnie wybierz **właściwości**.  
  
3.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.  
  
4.  Przenieś **usługi** projektu na początku listy, z **akcji "Start"**, a następnie przenieść **klienta** projektu po **usługi**projektu, także z **akcji "Start"**, więc **klienta** projektu jest wykonywany po **usługi** projektu.  
  
5.  Kliknij przycisk **OK**, a następnie naciśnij klawisz F5 (lub CTRL + F5), aby uruchomić przykład.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
