---
title: Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 5533393f759408002b83ba8ff485ba8229e921dd
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964632"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="501c2-102">Konfigurowanie usługi aktywacji procesów systemu Windows do użycia z programem Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="501c2-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="501c2-103">W tym temacie opisano kroki wymagane do skonfigurowania usługi aktywacji procesów systemu Windows (znanej także jako) w systemie Windows Vista do hostowania usług Windows Communication Foundation (WCF), które nie komunikują się za pośrednictwem protokołów sieciowych protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="501c2-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="501c2-104">W poniższych sekcjach opisano kroki tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="501c2-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="501c2-105">Zainstaluj (lub Potwierdź instalację) wymagane składniki aktywacji WCF.</span><span class="sxs-lookup"><span data-stu-id="501c2-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="501c2-106">Utwórz lokację WAS z powiązaniami protokołu sieciowego, których chcesz użyć, lub Dodaj nowe powiązanie protokołu do istniejącej lokacji.</span><span class="sxs-lookup"><span data-stu-id="501c2-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="501c2-107">Utwórz aplikację do hostowania usług i zezwól tej aplikacji na korzystanie z wymaganych protokołów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="501c2-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="501c2-108">Utwórz usługę WCF, która uwidacznia punkt końcowy inny niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="501c2-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="501c2-109">Konfigurowanie lokacji z powiązaniami innymi niż HTTP</span><span class="sxs-lookup"><span data-stu-id="501c2-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="501c2-110">Aby można było użyć powiązania inne niż HTTP z programem, należy dodać powiązanie witryny do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="501c2-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="501c2-111">Magazyn konfiguracji dla programu to plik applicationHost. config znajdujący się w katalogu%windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="501c2-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="501c2-112">Ten magazyn konfiguracji jest współużytkowany przez program i usługi IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="501c2-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="501c2-113">applicationHost. config to plik tekstowy XML, który można otworzyć za pomocą dowolnego standardowego edytora tekstu (takiego jak Notatnik).</span><span class="sxs-lookup"><span data-stu-id="501c2-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="501c2-114">Jednak narzędzie konfiguracji wiersza polecenia usług IIS 7,0 (Appcmd. exe) jest preferowanym sposobem dodawania powiązań witryn innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="501c2-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="501c2-115">Następujące polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web przy użyciu pliku Appcmd. exe (to polecenie jest wprowadzane jako pojedynczy wiersz).</span><span class="sxs-lookup"><span data-stu-id="501c2-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="501c2-116">To polecenie dodaje nowe powiązanie net. TCP do domyślnej witryny sieci Web przez dodanie wiersza wskazanego poniżej do pliku applicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="501c2-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="501c2-117">Umożliwienie aplikacji używania protokołów innych niż HTTP</span><span class="sxs-lookup"><span data-stu-id="501c2-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="501c2-118">Możesz włączyć lub wyłączyć poszczególne sieci protocolsat poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="501c2-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="501c2-119">Następujące polecenie ilustruje sposób włączania protokołów HTTP i net. TCP dla aplikacji działającej w `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="501c2-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="501c2-120">Listę włączonych protokołów można również ustawić w \<applicationDefaults > elementu konfiguracji XML witryny przechowywanej w pliku ApplicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="501c2-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="501c2-121">Poniższy kod XML z pliku applicationHost. config ilustruje lokację powiązaną z protokołami HTTP i innym niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="501c2-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="501c2-122">Dodatkowa konfiguracja wymagana do obsługi protokołów innych niż HTTP jest wywoływana z komentarzami.</span><span class="sxs-lookup"><span data-stu-id="501c2-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="501c2-123">Jeśli podjęto próbę aktywowania usługi przy użyciu programu w ramach aktywacji bez użycia protokołu HTTP i nie zainstalowano i skonfigurowano, może zostać wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="501c2-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="501c2-124">Jeśli widzisz ten błąd, upewnij się, że aktywacja nie HTTP została zainstalowana i skonfigurowana prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="501c2-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="501c2-125">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i Konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="501c2-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="501c2-126">Kompilowanie usługi WCF używanej przez program w ramach aktywacji niezwiązanej z protokołem HTTP</span><span class="sxs-lookup"><span data-stu-id="501c2-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="501c2-127">Po wykonaniu czynności związanych z instalacją i konfiguracją programu (zobacz [jak: Instalowanie i Konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), skonfigurowanie usługi do użycia w ramach aktywacji jest podobne do konfigurowania usługi hostowanej w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="501c2-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="501c2-128">Aby uzyskać szczegółowe instrukcje dotyczące kompilowania usługi WCF, zobacz [jak: Hostowanie usługi WCF w usłudze was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="501c2-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501c2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="501c2-129">See also</span></span>

- [<span data-ttu-id="501c2-130">Hosting w usłudze aktywacji procesów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="501c2-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="501c2-131">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="501c2-131">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
