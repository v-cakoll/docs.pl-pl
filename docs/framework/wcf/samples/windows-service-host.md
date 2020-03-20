---
title: Host usług systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143528"
---
# <a name="windows-service-host"></a>Host usług systemu Windows
W tym przykładzie przedstawiono usługę Windows Communication Foundation (WCF) hostowana w zarządzanej usłudze systemu Windows. Usługi systemu Windows są kontrolowane za pomocą apletu Usługi w **Panelu sterowania** i mogą być skonfigurowane do automatycznego uruchamiania po ponownym uruchomieniu systemu. Przykład składa się z programu klienckiego i programu usługi systemu Windows. Usługa jest implementowana jako program .exe i zawiera własny kod hostingu. W innych środowiskach hostingowych, takich jak Usługi aktywacji procesów systemu Windows (WAS) lub Internetowe Usługi Informacyjne (IIS), nie jest konieczne pisanie kodu hostingu.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po zbudowaniu tej usługi musi być zainstalowana za pomocą narzędzia Installutil.exe, jak każda inna usługa systemu Windows. Jeśli zamierzasz wprowadzić zmiany w usłudze, musisz `installutil /u`ją najpierw odinstalować za pomocą programu . Pliki Setup.bat i Cleanup.bat zawarte w tym przykładzie to polecenia instalowania i uruchamiania Usługi systemu Windows oraz zamykania i odinstalowywania usługi systemu Windows. Usługa WCF może odpowiadać na klientów tylko wtedy, gdy usługa systemu Windows jest uruchomiona. Jeśli usługa systemu Windows zostanie zatrzymana przy użyciu apletu <xref:System.ServiceModel.EndpointNotFoundException> Usługi z Panelu **sterowania** i uruchomisz klienta, wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi. Po ponownym uruchomieniu usługi systemu Windows i ponownym uruchomieniu klienta komunikacja zakończy się pomyślnie.  
  
 Kod usługi zawiera klasę instalatora, klasę implementacji usługi WCF, która implementuje kontrakt ICalculator i klasę usługi systemu Windows, która działa jako host w czasie wykonywania. Klasa instalatora, która dziedziczy po <xref:System.Configuration.Install.Installer>programie , umożliwia zainstalowanie programu jako usługi NT przez narzędzie Installutil.exe. Klasa implementacji `WcfCalculatorService`usługi , jest usługą WCF, która implementuje podstawową umowę serwisową. Ta usługa WCF jest hostowana wewnątrz `WindowsCalculatorService`klasy usługi systemu Windows o nazwie . Aby zakwalifikować się jako usługa systemu <xref:System.ServiceProcess.ServiceBase> Windows, <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> klasa <xref:System.ServiceProcess.ServiceBase.OnStop> dziedziczy i implementuje metody i. W <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> obiekt jest `WcfCalculatorService` tworzony dla typu i otwarty. W <xref:System.ServiceProcess.ServiceBase.OnStop>, ServiceHost jest zamknięty <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> przez <xref:System.ServiceModel.ServiceHost> wywołanie metody obiektu. Adres podstawowy hosta jest skonfigurowany przy użyciu elementu [ \<add>,](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) który jest elementem podrzędnym [ \<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), który jest elementem podrzędnym [ \<elementu>hosta,](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) który jest elementem podrzędnym [ \<elementu usługi>.](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
 Zdefiniowany punkt końcowy używa adresu podstawowego i [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). W poniższym przykładzie przedstawiono konfigurację adresu podstawowego, a także punktu końcowego, który udostępnia CalculatorService.  
  
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
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po utworzeniu rozwiązania uruchom plik Setup.bat z wiersza polecenia programu Visual Studio 2012 z podwyższonym poziomem uprawnień, aby zainstalować usługę systemu Windows za pomocą narzędzia Installutil.exe. Usługa powinna pojawić się w usługach.  
  
4. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też

- [AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
