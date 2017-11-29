---
title: "Host usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93f54c42637a2f4748b7835f527c9b0571d0883b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="windows-service-host"></a>Host usług systemu Windows
W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi hostowanej w usłudze zarządzanej systemu Windows. Usługi systemu Windows są kontrolowane za pomocą apletu usługi w **Panelu sterowania** i można je skonfigurować, aby uruchamiała się automatycznie po ponownym uruchomieniu systemu. Próbka składa się z programu klienckiego i program usługi systemu Windows. Usługa jest zaimplementowany jako program .exe i zawiera własną hostingu kod. W innych środowiskach hostingu, takich jak usługi aktywacji procesów systemu Windows (WAS) lub Internet Information Services (IIS), nie jest konieczne do pisania kodu hosting.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po utworzeniu tej usługi, musi być zainstalowany za pomocą narzędzia Installutil.exe podobnie jak inne usługi systemu Windows. Jeśli chcesz wprowadzić zmiany dotyczące usługi, należy najpierw odinstalować za pomocą `installutil /u`. Pliku Setup.bat i Cleanup.bat pliki uwzględnione w tym przykładzie przedstawiono polecenia zainstalować i uruchomić usługę systemu Windows, jak i do zamknięte i odinstalować usługi systemu Windows. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Usługa może odpowiedzieć tylko do klientów, jeśli usługa systemu Windows jest uruchomiona. Należy zatrzymać usługę systemu Windows za pomocą apletu usługi z **Panelu sterowania** a klientem, <xref:System.ServiceModel.EndpointNotFoundException> wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi. Jeśli ponowne uruchomienie usługi systemu Windows i uruchom ponownie klienta, komunikacja zakończy się pomyślnie.  
  
 Kod usługi zawiera klasę Instalatora [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasa implementacji usługi, która implementuje kontrakt ICalculator i klasy usługi systemu Windows, która działa jako host czasu wykonywania. Instalator klasy, która dziedziczy <xref:System.Configuration.Install.Installer>, pozwala programowi na narzędzie Installutil.exe instaluje jako usługa NT. Klasa implementacji usługi, `WcfCalculatorService`, jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa, która implementuje kontraktu usługi podstawowa. To [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi znajduje się wewnątrz klasy usługi systemu Windows o nazwie `WindowsCalculatorService`. Aby zakwalifikować się jako usługa systemu Windows, dziedziczy po klasie <xref:System.ServiceProcess.ServiceBase> i implementuje <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> i <xref:System.ServiceProcess.ServiceBase.OnStop> metody. W <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> obiekt jest tworzony dla `WcfCalculatorService` wpisz i otworzyć. W <xref:System.ServiceProcess.ServiceBase.OnStop>, ServiceHost jest zamknięty, wywołując <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metody <xref:System.ServiceModel.ServiceHost> obiektu. Adres podstawowy hosta jest konfigurowana przy użyciu [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, który jest elementem podrzędnym elementu [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), który jest elementem podrzędnym [ \<hosta >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, który jest elementem podrzędnym elementu [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu.  
  
 Adres podstawowy korzysta z punktu końcowego, który jest zdefiniowany i [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Poniższy przykład przedstawia konfigurację adres podstawowy, jak również punkt końcowy, który udostępnia CalculatorService.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po utworzeniu rozwiązania z podwyższonym poziomem uprawnień uruchom pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia, aby zainstalować usługę systemu Windows za pomocą narzędzia Installutil.exe. Usługa powinna pojawić się w usługach.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
