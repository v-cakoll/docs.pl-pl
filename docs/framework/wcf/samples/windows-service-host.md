---
title: Host usług systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 9c041f6e9505d2ec5865dd512359b497a411cb40
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602287"
---
# <a name="windows-service-host"></a>Host usług systemu Windows
Ten przykład pokazuje usługę Windows Communication Foundation (WCF) hostowaną w usłudze zarządzanej systemu Windows. Usługi systemu Windows są kontrolowane za pomocą apletu usługi w **Panelu sterowania** i można je skonfigurować do automatycznego uruchamiania po ponownym uruchomieniu systemu. Przykład składa się z programu klienckiego i programu usług systemu Windows. Usługa jest zaimplementowana jako program. exe i zawiera swój własny kod hostingu. W innych środowiskach hostingu, takich jak usługi aktywacji procesów systemu Windows (WAS) lub Internet Information Services (IIS), nie trzeba pisać kodu hostingu.

> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po skompilowaniu tej usługi należy ją zainstalować za pomocą narzędzia Installutil. exe, takiego jak jakakolwiek inna usługa systemu Windows. Jeśli chcesz wprowadzić zmiany w usłudze, musisz najpierw ją odinstalować za pomocą usługi `installutil /u` . Pliki Setup. bat i Oczyść. bat dołączone do tego przykładu są poleceniami służącymi do instalowania i uruchamiania usługi systemu Windows oraz do zamykania i odinstalowywania usługi systemu Windows. Usługa WCF może odpowiedzieć tylko na klientów, jeśli usługa systemu Windows jest uruchomiona. Jeśli zatrzymasz usługę systemu Windows przy użyciu apletu usługi w **Panelu sterowania** i uruchomisz klienta, <xref:System.ServiceModel.EndpointNotFoundException> wystąpi wyjątek, gdy klient próbuje uzyskać dostęp do usługi. Po ponownym uruchomieniu usługi systemu Windows, gdy ponownie zostanie uruchomiony klient, komunikacja powiedzie się.  
  
 Kod usługi zawiera klasę Instalatora, klasę implementacji usługi WCF implementującą kontrakt ICalculator oraz klasę usługi systemu Windows, która działa jako host czasu wykonywania. Klasa Instalatora, która dziedziczy po <xref:System.Configuration.Install.Installer> , umożliwia programowi zainstalowanie programu jako usługi NT za pomocą narzędzia Installutil. exe. Klasa implementacji usługi, `WcfCalculatorService` , jest usługą WCF implementującą podstawowy kontrakt usługi. Ta usługa WCF jest hostowana w klasie usługi systemu Windows o nazwie `WindowsCalculatorService` . Aby można było zakwalifikować jako usługę systemu Windows, Klasa dziedziczy z <xref:System.ServiceProcess.ServiceBase> i <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> implementuje <xref:System.ServiceProcess.ServiceBase.OnStop> metody i. W programie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> <xref:System.ServiceModel.ServiceHost> tworzony jest obiekt dla `WcfCalculatorService` typu i otwarty. W programie <xref:System.ServiceProcess.ServiceBase.OnStop> ServiceHost jest zamknięty przez wywołanie <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metody <xref:System.ServiceModel.ServiceHost> obiektu. Adres podstawowy hosta jest konfigurowany przy użyciu [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) elementu, który jest elementem podrzędnym [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) , który jest elementem podrzędnym [\<host>](../../configure-apps/file-schema/wcf/host.md) elementu, który jest elementem podrzędnym [\<service>](../../configure-apps/file-schema/wcf/service.md) elementu.  
  
 Zdefiniowany punkt końcowy używa adresu podstawowego i [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . Poniższy przykład pokazuje konfigurację adresu podstawowego, a także punkt końcowy, który uwidacznia CalculatorService.  
  
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
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Po skompilowaniu rozwiązania Uruchom plik Setup. bat z poziomu wiersza polecenia programu Visual Studio 2012 z podwyższonym poziomem uprawnień, aby zainstalować usługę systemu Windows za pomocą narzędzia Installutil. exe. Usługa powinna być widoczna w obszarze usługi.  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
