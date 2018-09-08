---
title: Aktywacja oparta na konfiguracji
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: e016dffdaf93b222c1fd2380bfa175256b009068
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188309"
---
# <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji
Niniejszy przykład pokazuje jak aktywować usług Windows Communication Foundation (WCF) bez konieczności plików .svc.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie klient jest w kliencie testowym WCF, a usługa jest hostowana w usługach IIS.  
  
> [!NOTE]
>  Instrukcje instalacji i kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Aktywacja usług bez konieczności pliku svc  
 W [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], plików .svc był wymagany do aktywacji usługi. Przyczyną jest dodatkowy nakład, ponieważ dodatkowy plik jest wymagany, które zostaną wdrożone i przechowywane wraz z aplikacji. Wraz z wydaniem [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], składniki aktywacji można skonfigurować przy użyciu pliku konfiguracji aplikacji.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] wprowadza nowy element konfiguracji (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) w polu <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> pliku konfiguracyjnego aplikacji. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekcja akceptuje kolekcja usług, aby aktywować tę funkcję, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Obserwowanie się jest Konfiguracja wygląda bardzo podobnie do konfigurowania plików .svc. Dodatkowe atrybutu, który został wprowadzony `relativeAddress` zawierający adres usługi. Względny adres jest również ścieżki wirtualnej dla usługi. Host pobiera plik z pliku Web.config `virtualPath` lokalizacji, jeśli obecny; w przeciwnym razie hosta przeszukuje jego rekursywnie folderu nadrzędnego.  
  
> [!NOTE]
>  Ten przykładowy skrypt wymaga hostowania w usługach IIS do funkcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik Service.csproj.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Przetestuj usługę, uruchamiając WCFTestClient.exe.  
  
4.  Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do folderu %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE.  
  
5.  Uruchom WcfTestClient.exe.  
  
6.  Ustaw adres wymiany Metadanych usługi.  
  
7.  Naciśnij klawisze CTRL + SHIFT + A, aby ustawić adres usługi.  
  
8.  Ustaw adres http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Wykonaj `Add` operacji. Ustaw wartość na `n1` parametr 10 i ustaw wartość na `n2` parametru na wartość 15.  
  
10. Naciśnij klawisz **wywołania**.  
  
     Oczekiwany wynik to 25.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po rozwiązaniu została skompilowana, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w usługach IIS. Katalog ServiceModelSamples teraz powinna zostać wyświetlona jako aplikację IIS.  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
