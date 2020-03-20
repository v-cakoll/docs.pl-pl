---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184250"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="652bb-102">Architektura aktywacji WAS</span><span class="sxs-lookup"><span data-stu-id="652bb-102">WAS Activation Architecture</span></span>
<span data-ttu-id="652bb-103">W tym temacie wyszczególnia i omówiono składniki usługi aktywacji procesów systemu Windows (znanej również jako WAS).</span><span class="sxs-lookup"><span data-stu-id="652bb-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="652bb-104">Składniki aktywacji</span><span class="sxs-lookup"><span data-stu-id="652bb-104">Activation Components</span></span>  
 <span data-ttu-id="652bb-105">WAS składa się z kilku elementów architektonicznych:</span><span class="sxs-lookup"><span data-stu-id="652bb-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="652bb-106">Adaptery odbiornika.</span><span class="sxs-lookup"><span data-stu-id="652bb-106">Listener adapters.</span></span> <span data-ttu-id="652bb-107">Usługi systemu Windows, które odbierają wiadomości na określonych protokołach sieciowych i komunikują się z usługą WAS w celu kierowania wiadomości przychodzących do właściwego procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="652bb-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="652bb-108">Został.</span><span class="sxs-lookup"><span data-stu-id="652bb-108">WAS.</span></span> <span data-ttu-id="652bb-109">Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.</span><span class="sxs-lookup"><span data-stu-id="652bb-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="652bb-110">Ogólny proces roboczy wykonywalny (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="652bb-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="652bb-111">Menedżer aplikacji.</span><span class="sxs-lookup"><span data-stu-id="652bb-111">Application manager.</span></span> <span data-ttu-id="652bb-112">Zarządza tworzeniem i okresem istnienia domen aplikacji, które hostuje aplikacje w procesie roboczym.</span><span class="sxs-lookup"><span data-stu-id="652bb-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="652bb-113">Programy obsługi protokołu.</span><span class="sxs-lookup"><span data-stu-id="652bb-113">Protocol handlers.</span></span> <span data-ttu-id="652bb-114">Składniki specyficzne dla protokołu, które działają w procesie roboczym i zarządzają komunikacją między procesem roboczym a poszczególnymi kartami odbiornika.</span><span class="sxs-lookup"><span data-stu-id="652bb-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="652bb-115">Istnieją dwa typy programów obsługi protokołów: programy obsługi protokołów procesów i programy obsługi protokołu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="652bb-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="652bb-116">Gdy usługa WAS aktywuje wystąpienie procesu roboczego, ładuje programy obsługi protokołu procesu wymagane do procesu roboczego i używa menedżera aplikacji do utworzenia domeny aplikacji do obsługi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="652bb-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="652bb-117">Domena aplikacji ładuje kod aplikacji, a także programy obsługi protokołu AppDomain, których wymagają protokoły sieciowe używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="652bb-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Zrzut ekranu przedstawiający architekturę WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="652bb-119">Adaptery odbiornika</span><span class="sxs-lookup"><span data-stu-id="652bb-119">Listener Adapters</span></span>  
 <span data-ttu-id="652bb-120">Karty odbiornika to pojedyncze usługi systemu Windows, które implementują logikę komunikacji sieciowej używaną do odbierania wiadomości przy użyciu protokołu sieciowego, na który nasłuchują.</span><span class="sxs-lookup"><span data-stu-id="652bb-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="652bb-121">W poniższej tabeli wymieniono karty odbiornika dla protokołów Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="652bb-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="652bb-122">Nazwa usługi karty odbiornika</span><span class="sxs-lookup"><span data-stu-id="652bb-122">Listener adapter service name</span></span>|<span data-ttu-id="652bb-123">Protocol (Protokół)</span><span class="sxs-lookup"><span data-stu-id="652bb-123">Protocol</span></span>|<span data-ttu-id="652bb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="652bb-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="652bb-125">W3svc</span><span class="sxs-lookup"><span data-stu-id="652bb-125">W3SVC</span></span>|<span data-ttu-id="652bb-126">http</span><span class="sxs-lookup"><span data-stu-id="652bb-126">http</span></span>|<span data-ttu-id="652bb-127">Typowy składnik, który zapewnia aktywację HTTP dla usług IIS 7.0 i WCF.</span><span class="sxs-lookup"><span data-stu-id="652bb-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="652bb-128">NetTcpActivator (NetTcpActivator)</span><span class="sxs-lookup"><span data-stu-id="652bb-128">NetTcpActivator</span></span>|<span data-ttu-id="652bb-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="652bb-129">net.tcp</span></span>|<span data-ttu-id="652bb-130">Zależy od usługi NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="652bb-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="652bb-131">NetPipeActivator (NetPipeActivator)</span><span class="sxs-lookup"><span data-stu-id="652bb-131">NetPipeActivator</span></span>|<span data-ttu-id="652bb-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="652bb-132">net.pipe</span></span>||  
|<span data-ttu-id="652bb-133">NetMsmqActivator (Aktywizm NetMsmq)</span><span class="sxs-lookup"><span data-stu-id="652bb-133">NetMsmqActivator</span></span>|<span data-ttu-id="652bb-134">Net.msmq</span><span class="sxs-lookup"><span data-stu-id="652bb-134">net.msmq</span></span>|<span data-ttu-id="652bb-135">Do użytku z aplikacjami usługi kolejkowania wiadomości opartymi na WCF.</span><span class="sxs-lookup"><span data-stu-id="652bb-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="652bb-136">NetMsmqActivator (Aktywizm NetMsmq)</span><span class="sxs-lookup"><span data-stu-id="652bb-136">NetMsmqActivator</span></span>|<span data-ttu-id="652bb-137">nazwa msmq.format</span><span class="sxs-lookup"><span data-stu-id="652bb-137">msmq.formatname</span></span>|<span data-ttu-id="652bb-138">Zapewnia zgodność z powrotem z istniejącymi aplikacjami Usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="652bb-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="652bb-139">Karty odbiornika dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost.config, jak pokazano w poniższym przykładzie XML.</span><span class="sxs-lookup"><span data-stu-id="652bb-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="652bb-140">Programy obsługi protokołów</span><span class="sxs-lookup"><span data-stu-id="652bb-140">Protocol Handlers</span></span>  
 <span data-ttu-id="652bb-141">Programy obsługi protokołów Process i AppDomain dla określonych protokołów są rejestrowane w pliku Web.config na poziomie komputera.</span><span class="sxs-lookup"><span data-stu-id="652bb-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="652bb-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="652bb-142">See also</span></span>

- [<span data-ttu-id="652bb-143">Konfigurowanie usługi WAS do użycia z programem WCF</span><span class="sxs-lookup"><span data-stu-id="652bb-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="652bb-144">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="652bb-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
