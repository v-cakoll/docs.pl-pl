---
title: Aktywacja oparta na konfiguracji
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809917"
---
# <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji
W tym przykładzie pokazano, jak można aktywować usługi Windows Communication Foundation (WCF) bez konieczności pliku svc.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie klient jest klienta testowego WCF, a usługa jest obsługiwana w usługach IIS.  
  
> [!NOTE]
>  Instrukcje instalacji i kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Aktywacja usług bez konieczności pliku svc  
 W [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], pliku svc nie jest wymagana do aktywacji usługi. Przyczyną narzut na dodatkowe zarządzanie, ponieważ dodatkowy plik nie jest wymagana, aby wdrożyć i przechowywane wraz z aplikacji. Wraz z wydaniem [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], można skonfigurować składniki aktywacji przy użyciu pliku konfiguracji aplikacji.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] wprowadzono nowy element konfiguracji (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) w <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> pliku konfiguracyjnego aplikacji. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekcja akceptuje kolekcja usług do aktywacji, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Obserwacji dokonanie jest Konfiguracja wygląda bardzo podobnie do konfigurowania plików .svc. Atrybut dodatkowe wprowadzone jest `relativeAddress` zapewnia adresu usługi. Adres względny jest również ścieżki wirtualnej dla usługi. Host pobiera plik z pliku Web.config `virtualPath` lokalizacji, jeśli występuje; w przeciwnym razie hosta wyszukuje jego rekursywnie folderu nadrzędnego.  
  
> [!NOTE]
>  W tym przykładzie wymaga hosting w usługach IIS funkcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik Service.csproj.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Przetestuj usługę uruchamiając WCFTestClient.exe.  
  
4.  Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do folderu 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.  
  
5.  Uruchom WcfTestClient.exe.  
  
6.  Ustaw adres MEX usługi.  
  
7.  Naciśnij klawisze CTRL + SHIFT + A, aby ustawić adres usługi.  
  
8.  Ustaw adres http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Wykonaj `Add` operacji. Ustaw wartość na `n1` parametru 10 i ustaw wartość na `n2` parametru do 15.  
  
10. Naciśnij klawisz **wywołania**.  
  
     Oczekiwany wynik to 25.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po rozwiązaniu został utworzony, uruchom pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS. Katalog ServiceModelSamples powinien zostać wyświetlony jako aplikacja IIS.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
