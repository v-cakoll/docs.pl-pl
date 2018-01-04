---
title: "Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
W tym temacie opisano kroki wymagane do skonfigurowania Windows Process Activation Service (znanej także jako Usługa WAS) w [!INCLUDE[wv](../../../../includes/wv-md.md)] hosta [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoły sieciowe usług, które nie komunikują się za pośrednictwem protokołu HTTP. W poniższych sekcjach opisano czynności dla tej konfiguracji:  
  
-   Zainstaluj (lub potwierdź instalacji) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymagane składniki aktywacji.  
  
-   Utwórz witrynę WAS z powiązań protokołów sieciowych, które mają być używane, lub Dodaj nowe powiązanie protokołu do istniejącej lokacji.  
  
-   Utwórz aplikację do obsługi usług i Włącz tej aplikacji do korzystania z protokołów sieciowych wymaganych.  
  
-   Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi udostępniającej punkt końcowy protokołu HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurowanie lokacji z powiązaniami bez HTTP  
 Aby używać powiązania protokołu HTTP z WAS, należy dodać powiązania witryny konfiguracji WAS. Magazyn konfiguracji dla WAS jest plik applicationHost.config, znajduje się w katalogu %windir%\system32\inetsrv\config. Tego magazynu konfiguracji jest współużytkowany przez usługi IIS 7.0 i WAS.  
  
 applicationHost.config jest plik tekstowy XML, który można otworzyć za pomocą dowolnego edytora tekstu standardowego (np. Notatnika). Jednak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzia wiersza polecenia konfiguracji (appcmd.exe) jest preferowany sposób dodawania powiązania protokołu HTTP witryny.  
  
 Polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web przy użyciu appcmd.exe (to polecenie jest wprowadzana jako jeden wiersz).  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 To polecenie dodaje nowe powiązanie net.tcp do domyślnej witryny sieci Web, dodając wiersz wymienione poniżej do pliku applicationHost.config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Włączanie aplikacji do korzystania z protokołów innych niż HTTP  
 Można włączyć lub wyłączyć poszczególne sieci protocolsat na poziomie aplikacji. Polecenie ilustruje sposób Włącz protokoły HTTP i net.tcp dla aplikacji, która działa w `Default Web Site`.  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Lista włączone protokoły można też ustawić w \<applicationDefaults > element konfiguracji XML witryny przechowywane w pliku ApplicationHost.config.  
  
 Następujący kod XML w pliku applicationHost.config przedstawiono lokacji powiązane z protokołów HTTP i protokołów innych niż HTTP. Dodatkowej konfiguracji, które są wymagane do obsługi protokołów innych niż HTTP nazywa z komentarzami.  
  
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
  
 Jeśli próba uaktywnienia usługą za pomocą usługi WAS dla Aktywacja bez HTTP i nie zostanie zainstalowany i skonfigurowany WAS może zostać wyświetlony następujący błąd:  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Jeśli zostanie wyświetlony ten błąd, upewnij się, Usługa WAS dla Aktywacja bez HTTP jest zainstalowany i prawidłowo skonfigurowany. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Tworzenie usługi WCF usługi czy używa DOTYCZYŁO Aktywacja bez HTTP  
 Po wykonaniu czynności, aby zainstalować i skonfigurować WAS (zobacz [porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), skonfigurowanie usługi do użycia WAS aktywacji jest podobne do konfigurowania usługi hostowanej w usługach IIS.  
  
 Szczegółowe instrukcje dotyczące tworzenia aktywowany WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting w usłudze aktywacji procesów systemu Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
