---
title: "Fabryka kanałów konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa0f4aec0a673a07c6b6d752d8609caedbcfa4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-channel-factory"></a>Fabryka kanałów konfiguracji
W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Umożliwia centralne zarządzanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfiguracji klienta. Może to być również przydatne w scenariuszach, w których konfiguracja jest wybrane lub zmienić po czas ładowania domeny aplikacji.  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
