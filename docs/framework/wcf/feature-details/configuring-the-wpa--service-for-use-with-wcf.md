---
title: Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 3a4d771c3f2d5e7e6ec4fd6a1e229548e063a6d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="b17bb-102">Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b17bb-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="b17bb-103">W tym temacie opisano kroki wymagane do skonfigurowania Windows Process Activation Service (znanej także jako Usługa WAS) w [!INCLUDE[wv](../../../../includes/wv-md.md)] do obsługi systemu Windows Communication Foundation (WCF) protokołów sieciowych usług, które nie komunikują się za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b17bb-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="b17bb-104">W poniższych sekcjach opisano czynności dla tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b17bb-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="b17bb-105">Zainstaluj (lub potwierdź instalacji) składników aktywacji programu WCF, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="b17bb-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="b17bb-106">Utwórz witrynę WAS z powiązań protokołów sieciowych, które mają być używane, lub Dodaj nowe powiązanie protokołu do istniejącej lokacji.</span><span class="sxs-lookup"><span data-stu-id="b17bb-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="b17bb-107">Utwórz aplikację do obsługi usług i Włącz tej aplikacji do korzystania z protokołów sieciowych wymaganych.</span><span class="sxs-lookup"><span data-stu-id="b17bb-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="b17bb-108">Tworzenie usługi WCF ujawniający punkt końcowy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b17bb-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="b17bb-109">Konfigurowanie lokacji z powiązaniami bez HTTP</span><span class="sxs-lookup"><span data-stu-id="b17bb-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="b17bb-110">Aby używać powiązania protokołu HTTP z WAS, należy dodać powiązania witryny konfiguracji WAS.</span><span class="sxs-lookup"><span data-stu-id="b17bb-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="b17bb-111">Magazyn konfiguracji dla WAS jest plik applicationHost.config, znajduje się w katalogu %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="b17bb-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="b17bb-112">Tego magazynu konfiguracji jest współużytkowany przez usługi IIS 7.0 i WAS.</span><span class="sxs-lookup"><span data-stu-id="b17bb-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="b17bb-113">applicationHost.config jest plik tekstowy XML, który można otworzyć za pomocą dowolnego edytora tekstu standardowego (np. Notatnika).</span><span class="sxs-lookup"><span data-stu-id="b17bb-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="b17bb-114">Jednak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzia wiersza polecenia konfiguracji (appcmd.exe) jest preferowany sposób dodawania powiązania protokołu HTTP witryny.</span><span class="sxs-lookup"><span data-stu-id="b17bb-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="b17bb-115">Polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web przy użyciu appcmd.exe (to polecenie jest wprowadzana jako jeden wiersz).</span><span class="sxs-lookup"><span data-stu-id="b17bb-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="b17bb-116">To polecenie dodaje nowe powiązanie net.tcp do domyślnej witryny sieci Web, dodając wiersz wymienione poniżej do pliku applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="b17bb-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="b17bb-117">Włączanie aplikacji do korzystania z protokołów innych niż HTTP</span><span class="sxs-lookup"><span data-stu-id="b17bb-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="b17bb-118">Można włączyć lub wyłączyć poszczególne sieci protocolsat na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b17bb-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="b17bb-119">Polecenie ilustruje sposób Włącz protokoły HTTP i net.tcp dla aplikacji, która działa w `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="b17bb-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="b17bb-120">Lista włączone protokoły można też ustawić w \<applicationDefaults > element konfiguracji XML witryny przechowywane w pliku ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="b17bb-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="b17bb-121">Następujący kod XML w pliku applicationHost.config przedstawiono lokacji powiązane z protokołów HTTP i protokołów innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="b17bb-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="b17bb-122">Dodatkowej konfiguracji, które są wymagane do obsługi protokołów innych niż HTTP nazywa z komentarzami.</span><span class="sxs-lookup"><span data-stu-id="b17bb-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="b17bb-123">Jeśli próba uaktywnienia usługą za pomocą usługi WAS dla Aktywacja bez HTTP i nie zostanie zainstalowany i skonfigurowany WAS może zostać wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="b17bb-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="b17bb-124">Jeśli zostanie wyświetlony ten błąd, upewnij się, Usługa WAS dla Aktywacja bez HTTP jest zainstalowany i prawidłowo skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="b17bb-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="b17bb-125">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="b17bb-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="b17bb-126">Tworzenie usługi WCF usługi czy używa DOTYCZYŁO Aktywacja bez HTTP</span><span class="sxs-lookup"><span data-stu-id="b17bb-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="b17bb-127">Po wykonaniu czynności, aby zainstalować i skonfigurować WAS (zobacz [porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), skonfigurowanie usługi do użycia WAS aktywacji jest podobne do konfigurowania usługi hostowanej w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="b17bb-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="b17bb-128">Aby uzyskać szczegółowe instrukcje dotyczące tworzenia usługi WAS została aktywowana WCF, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="b17bb-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17bb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b17bb-129">See Also</span></span>  
 [<span data-ttu-id="b17bb-130">Hosting w usłudze aktywacji procesów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b17bb-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [<span data-ttu-id="b17bb-131">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="b17bb-131">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
