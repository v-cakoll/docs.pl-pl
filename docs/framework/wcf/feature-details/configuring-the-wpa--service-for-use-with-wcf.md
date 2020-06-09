---
title: Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 06d3a7bd798913b06d342ac09d12e736fc436b3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597504"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej także jako) w systemie Windows Vista do hostowania usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych protokołu HTTP. W poniższych sekcjach opisano kroki tej konfiguracji:  
  
- Zainstaluj (lub Potwierdź instalację) wymagane składniki aktywacji WCF.  
  
- Utwórz lokację WAS z powiązaniami protokołu sieciowego, których chcesz użyć, lub Dodaj nowe powiązanie protokołu do istniejącej lokacji.  
  
- Utwórz aplikację do hostowania usług i zezwól tej aplikacji na korzystanie z wymaganych protokołów sieciowych.  
  
- Utwórz usługę WCF, która uwidacznia punkt końcowy inny niż HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurowanie lokacji z powiązaniami innymi niż HTTP  
 Aby można było użyć powiązania inne niż HTTP z programem, należy dodać powiązanie witryny do konfiguracji. Magazyn konfiguracji dla programu to plik applicationHost. config znajdujący się w katalogu%windir%\system32\inetsrv\config. Ten magazyn konfiguracji jest współużytkowany przez program i usługi IIS 7,0.  
  
 applicationHost. config to plik tekstowy XML, który można otworzyć za pomocą dowolnego standardowego edytora tekstu (takiego jak Notatnik). Jednak narzędzie konfiguracji wiersza polecenia usług IIS 7,0 (Appcmd. exe) jest preferowanym sposobem dodawania powiązań witryn innych niż HTTP.  
  
 Następujące polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web przy użyciu pliku Appcmd. exe (to polecenie jest wprowadzane jako pojedynczy wiersz).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 To polecenie dodaje nowe powiązanie net. TCP do domyślnej witryny sieci Web przez dodanie wiersza wskazanego poniżej do pliku applicationHost. config.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Umożliwienie aplikacji używania protokołów innych niż HTTP  
 Możesz włączyć lub wyłączyć poszczególne sieci protocolsat poziomu aplikacji. Następujące polecenie ilustruje sposób włączania protokołów HTTP i net. TCP dla aplikacji, która działa w `Default Web Site` .  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Listę włączonych protokołów można również ustawić w \<applicationDefaults> elemencie konfiguracji XML lokacji przechowywanej w pliku ApplicationHost. config.  
  
 Poniższy kod XML z pliku applicationHost. config ilustruje lokację powiązaną z protokołami HTTP i innym niż HTTP. Dodatkowa konfiguracja wymagana do obsługi protokołów innych niż HTTP jest wywoływana z komentarzami.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Jeśli podjęto próbę aktywowania usługi przy użyciu programu w ramach aktywacji bez użycia protokołu HTTP i nie zainstalowano i skonfigurowano, może zostać wyświetlony następujący błąd:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Jeśli widzisz ten błąd, upewnij się, że aktywacja nie HTTP została zainstalowana i skonfigurowana prawidłowo. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i Konfigurowanie składników aktywacji programu WCF](how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Kompilowanie usługi WCF używanej przez program w ramach aktywacji niezwiązanej z protokołem HTTP  
 Po wykonaniu czynności związanych z instalacją i konfiguracją programu (zobacz [jak: Instalowanie i Konfigurowanie składników aktywacji programu WCF](how-to-install-and-configure-wcf-activation-components.md)), skonfigurowanie usługi do użycia w ramach aktywacji jest podobne do konfigurowania usługi hostowanej w usługach IIS.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące kompilowania usługi WCF, zobacz [jak: Hostowanie usługi WCF w usłudze was](how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Zobacz też

- [Hosting w usłudze aktywacji procesów systemu Windows](hosting-in-windows-process-activation-service.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
