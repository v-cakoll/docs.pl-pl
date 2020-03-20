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
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="13c93-102">Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="13c93-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="13c93-103">W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej również jako WAS) w systemie Windows Vista do obsługi usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c93-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="13c93-104">W poniższych sekcjach opisano kroki dotyczące tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="13c93-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="13c93-105">Zainstaluj (lub potwierdź instalację) wymaganych komponentów aktywacji WCF.</span><span class="sxs-lookup"><span data-stu-id="13c93-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="13c93-106">Utwórz witrynę WAS z powiązaniami protokołu sieciowego, których chcesz użyć, lub dodaj nowe powiązanie protokołu do istniejącej lokacji.</span><span class="sxs-lookup"><span data-stu-id="13c93-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="13c93-107">Utwórz aplikację do obsługi usług i włącz tę aplikację do korzystania z wymaganych protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="13c93-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="13c93-108">Tworzenie usługi WCF, która udostępnia punkt końcowy nie-HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c93-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="13c93-109">Konfigurowanie witryny z powiązaniami innych niż HTTP</span><span class="sxs-lookup"><span data-stu-id="13c93-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="13c93-110">Aby użyć powiązania innego niż HTTP z was, powiązanie lokacji musi zostać dodane do konfiguracji WAS.</span><span class="sxs-lookup"><span data-stu-id="13c93-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="13c93-111">Magazyn konfiguracji usługi WAS to plik applicationHost.config, znajdujący się w katalogu %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="13c93-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="13c93-112">Ten magazyn konfiguracji jest współużytkowane przez usługi WAS i usługi IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="13c93-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="13c93-113">applicationHost.config to plik tekstowy XML, który można otworzyć za pomocą dowolnego standardowego edytora tekstu (takiego jak Notatnik).</span><span class="sxs-lookup"><span data-stu-id="13c93-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="13c93-114">Jednak narzędzie konfiguracji wiersza polecenia usług IIS 7.0 (appcmd.exe) jest preferowanym sposobem dodawania powiązań lokacji innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c93-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="13c93-115">Następujące polecenie dodaje powiązanie lokacji net.tcp do domyślnej witryny sieci Web przy użyciu programu appcmd.exe (to polecenie jest wprowadzane jako pojedynczy wiersz).</span><span class="sxs-lookup"><span data-stu-id="13c93-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="13c93-116">To polecenie dodaje nowe powiązanie net.tcp do domyślnej witryny sieci Web, dodając wiersz wskazany poniżej do pliku applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="13c93-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="13c93-117">Włączanie aplikacji do używania protokołów innych niż HTTP</span><span class="sxs-lookup"><span data-stu-id="13c93-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="13c93-118">Można włączyć lub wyłączyć poszczególne protokoły sieciowena poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13c93-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="13c93-119">Poniższe polecenie ilustruje sposób włączania zarówno protokołów HTTP, jak i `Default Web Site`net.tcp dla aplikacji uruchamianej w pliku .</span><span class="sxs-lookup"><span data-stu-id="13c93-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="13c93-120">Listę włączonych protokołów można również ustawić \<w aplikacjiDefaults> element konfiguracji XML witryny przechowywane w ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="13c93-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="13c93-121">Poniższy kod XML z aplikacjiHost.config ilustruje witrynę powiązaną z protokołami HTTP i innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c93-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="13c93-122">Dodatkowa konfiguracja wymagana do obsługi protokołów innych niż HTTP jest wywoływana z komentarzami.</span><span class="sxs-lookup"><span data-stu-id="13c93-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="13c93-123">Jeśli spróbujesz aktywować usługę przy użyciu funkcji WAS dla aktywacji innych niż HTTP, a nie zainstalowano i nie skonfigurowano usługi WAS, może zostać wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="13c93-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="13c93-124">Jeśli widzisz ten błąd upewnij się, że był dla aktywacji innych niż HTTP jest zainstalowany i poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="13c93-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="13c93-125">Aby uzyskać więcej informacji, zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="13c93-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="13c93-126">Tworzenie usługi WCF, która używa usługi WAS do aktywacji innych niż HTTP</span><span class="sxs-lookup"><span data-stu-id="13c93-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="13c93-127">Po wykonaniu czynności związanych z instalacją i skonfigurowaniem usługi WAS (zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF), konfigurowanie](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)usługi do aktywacji usługi WAS jest podobne do konfigurowania usługi hostowanego w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="13c93-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="13c93-128">Aby uzyskać szczegółowe instrukcje dotyczące tworzenia usługi WCF aktywowane przez USŁUGĘ, zobacz [Jak: Hostować usługę WCF w was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="13c93-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c93-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c93-129">See also</span></span>

- [<span data-ttu-id="13c93-130">Hosting w usłudze aktywacji procesów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="13c93-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="13c93-131">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="13c93-131">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
