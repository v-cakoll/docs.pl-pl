---
title: Aktywacja oparta na konfiguracji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db67447ce262949c9ad302a37420fc7023264bd2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji
W tym przykładzie pokazano, jak aktywować [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług bez konieczności pliku svc.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie klient jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] testu klient i usługa znajduje się w usługach IIS.  
  
> [!NOTE]
>  Instrukcje instalacji i kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Aktywacja usług bez konieczności pliku svc  
 W [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], pliku svc nie jest wymagana do aktywacji usługi. Przyczyną narzut na dodatkowe zarządzanie, ponieważ dodatkowy plik nie jest wymagana, aby wdrożyć i przechowywane wraz z aplikacji. Wraz z wydaniem [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], można skonfigurować składniki aktywacji przy użyciu pliku konfiguracji aplikacji.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]wprowadzono nowy element konfiguracji (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) w <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> pliku konfiguracyjnego aplikacji. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekcja akceptuje kolekcja usług do aktywacji, jak pokazano w poniższym przykładzie kodu.  
  
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
  
8.  Ustawić adres http://localhost/ServiceModelSamples/Calculator.svc.  
  
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
