---
title: Host usług systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 65797863fc8187ffebbcb660e9fb285bfa1aabd0
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583857"
---
# <a name="windows-service-host"></a>Host usług systemu Windows
Niniejszy przykład pokazuje usługi Windows Communication Foundation (WCF), hostowana w zarządzanych usług Windows. Usługi Windows są kontrolowane za pomocą apletu usługi w **Panelu sterowania** i można je skonfigurować, aby uruchamiała się automatycznie po ponownym uruchomieniu systemu. Przykład składa się z program kliencki i programów usługi Windows. Ta usługa jest implementowany jako .exe program i zawiera swój własny kod hostingu. W innych środowiskach hostingu, takich jak Windows Process Activation usług (WAS) lub Internet Information Services (IIS) nie jest konieczne pisanie kod hostingu.

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po utworzeniu tej usługi, musi być zainstalowany przy użyciu narzędzia Installutil.exe, takie jak dowolnej innej usługi Windows. Jeśli chcesz wprowadzić zmiany do usługi, należy najpierw odinstalować ją za pomocą `installutil /u`. Pliki Setup.bat i Cleanup.bat, zawarty w tym przykładzie są polecenia do instalowania i uruchamiania usługi Windows i zamknij, a następnie odinstaluj usługę Windows. Usługi WCF tylko może odpowiadać na klientach, jeśli usługa Windows jest uruchomiona. Należy zatrzymać usługę Windows za pomocą apletu usługi z **Panelu sterowania** i uruchomienia klienta <xref:System.ServiceModel.EndpointNotFoundException> wystąpi wyjątek, gdy klient próbuje uzyskać dostęp do usługi. Jeśli ponownie uruchom usługę Windows, a następnie ponownie uruchomić klienta, komunikacja zakończy się pomyślnie.  
  
 Kod usługi zawiera klasę Instalatora, klasa implementacji usługi WCF, która implementuje ten kontrakt ICalculator i klasa usługi Windows, która działa jako host środowiska wykonawczego. Klasa Instalatora, która dziedziczy z <xref:System.Configuration.Install.Installer>, umożliwia uruchamianie programu można zainstalować jako usługi NT przez narzędzie Installutil.exe. Klasa implementacji usługi, `WcfCalculatorService`, to usługa WCF, która implementuje kontraktu usługi podstawowa. Ta usługa WCF znajduje się wewnątrz klasy usługi Windows o nazwie `WindowsCalculatorService`. Aby zakwalifikować się jako usługa Windows, klasa dziedziczy <xref:System.ServiceProcess.ServiceBase> i implementuje <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> i <xref:System.ServiceProcess.ServiceBase.OnStop> metody. W <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> obiekt zostanie utworzony dla `WcfCalculatorService` wpisz i otwarty. W <xref:System.ServiceProcess.ServiceBase.OnStop>, elementu ServiceHost jest zamknięty przez wywołanie metody <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metody <xref:System.ServiceModel.ServiceHost> obiektu. Podstawowy adres hosta jest skonfigurowany przy użyciu [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, który jest elementem podrzędnym elementu [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), który jest elementem podrzędnym [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, który jest elementem podrzędnym elementu [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu.  
  
 Punkt końcowy, który jest zdefiniowany korzysta z adresu podstawowego i [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Poniższy przykład przedstawia konfigurację adres podstawowy, jak również punkt końcowy, który udostępnia CalculatorService.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po rozwiązaniu została skompilowana, uruchom Setup.bat Visual Studio 2012 w wierszu polecenia z podwyższonym zainstalować usługę Windows, za pomocą narzędzie Installutil.exe. Usługa powinna pojawić się w usługach.  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
