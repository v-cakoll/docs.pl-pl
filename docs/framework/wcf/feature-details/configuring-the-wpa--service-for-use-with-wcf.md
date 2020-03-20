---
title: Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 2da2653f3d2bd3d998b0ebbe87ea33760315f7df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185304"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej również jako WAS) w systemie Windows Vista do obsługi usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych HTTP. W poniższych sekcjach opisano kroki dotyczące tej konfiguracji:  
  
- Zainstaluj (lub potwierdź instalację) wymaganych komponentów aktywacji WCF.  
  
- Utwórz witrynę WAS z powiązaniami protokołu sieciowego, których chcesz użyć, lub dodaj nowe powiązanie protokołu do istniejącej lokacji.  
  
- Utwórz aplikację do obsługi usług i włącz tę aplikację do korzystania z wymaganych protokołów sieciowych.  
  
- Tworzenie usługi WCF, która udostępnia punkt końcowy nie-HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurowanie witryny z powiązaniami innych niż HTTP  
 Aby użyć powiązania innego niż HTTP z was, powiązanie lokacji musi zostać dodane do konfiguracji WAS. Magazyn konfiguracji usługi WAS to plik applicationHost.config, znajdujący się w katalogu %windir%\system32\inetsrv\config. Ten magazyn konfiguracji jest współużytkowane przez usługi WAS i usługi IIS 7.0.  
  
 applicationHost.config to plik tekstowy XML, który można otworzyć za pomocą dowolnego standardowego edytora tekstu (takiego jak Notatnik). Jednak narzędzie konfiguracji wiersza polecenia usług IIS 7.0 (appcmd.exe) jest preferowanym sposobem dodawania powiązań lokacji innych niż HTTP.  
  
 Następujące polecenie dodaje powiązanie lokacji net.tcp do domyślnej witryny sieci Web przy użyciu programu appcmd.exe (to polecenie jest wprowadzane jako pojedynczy wiersz).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 To polecenie dodaje nowe powiązanie net.tcp do domyślnej witryny sieci Web, dodając wiersz wskazany poniżej do pliku applicationHost.config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Włączanie aplikacji do używania protokołów innych niż HTTP  
 Można włączyć lub wyłączyć poszczególne protokoły sieciowena poziomie aplikacji. Poniższe polecenie ilustruje sposób włączania zarówno protokołów HTTP, jak i `Default Web Site`net.tcp dla aplikacji uruchamianej w pliku .  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Listę włączonych protokołów można również ustawić \<w aplikacjiDefaults> element konfiguracji XML witryny przechowywane w ApplicationHost.config.  
  
 Poniższy kod XML z aplikacjiHost.config ilustruje witrynę powiązaną z protokołami HTTP i innych niż HTTP. Dodatkowa konfiguracja wymagana do obsługi protokołów innych niż HTTP jest wywoływana z komentarzami.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
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
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Jeśli spróbujesz aktywować usługę przy użyciu funkcji WAS dla aktywacji innych niż HTTP, a nie zainstalowano i nie skonfigurowano usługi WAS, może zostać wyświetlony następujący błąd:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Jeśli widzisz ten błąd upewnij się, że był dla aktywacji innych niż HTTP jest zainstalowany i poprawnie skonfigurowany. Aby uzyskać więcej informacji, zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Tworzenie usługi WCF, która używa usługi WAS do aktywacji innych niż HTTP  
 Po wykonaniu czynności związanych z instalacją i skonfigurowaniem usługi WAS (zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF), konfigurowanie](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)usługi do aktywacji usługi WAS jest podobne do konfigurowania usługi hostowanego w usługach IIS.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące tworzenia usługi WCF aktywowane przez USŁUGĘ, zobacz [Jak: Hostować usługę WCF w was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Zobacz też

- [Hosting w usłudze aktywacji procesów systemu Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
