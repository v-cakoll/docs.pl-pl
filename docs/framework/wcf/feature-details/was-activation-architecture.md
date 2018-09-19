---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 64219649e7b743b7dd3a67673c3f2409aeeba486
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008649"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="8cb7a-102">Architektura aktywacji WAS</span><span class="sxs-lookup"><span data-stu-id="8cb7a-102">WAS Activation Architecture</span></span>
<span data-ttu-id="8cb7a-103">W tym temacie wyszczególniono oraz omówienie składników usługi aktywacji procesów systemu Windows (znany także jako WAS).</span><span class="sxs-lookup"><span data-stu-id="8cb7a-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="8cb7a-104">Składniki aktywacji</span><span class="sxs-lookup"><span data-stu-id="8cb7a-104">Activation Components</span></span>  
 <span data-ttu-id="8cb7a-105">ZOSTAŁ składa się z kilku składników architektury:</span><span class="sxs-lookup"><span data-stu-id="8cb7a-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="8cb7a-106">Odbiornik kart.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-106">Listener adapters.</span></span> <span data-ttu-id="8cb7a-107">Usługi Windows odbierać wiadomości od określonych protokołów sieciowych, które komunikują się z WAS do rozsyłania wiadomości przychodzących do procesu roboczego poprawne.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="8cb7a-108">BYŁO.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-108">WAS.</span></span> <span data-ttu-id="8cb7a-109">Usługa Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="8cb7a-110">Ogólny proces pliku wykonywalnego procesu roboczego (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="8cb7a-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="8cb7a-111">Menedżer aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-111">Application manager.</span></span> <span data-ttu-id="8cb7a-112">Zarządza tworzeniem i okresem istnienia domen aplikacji, które przetwarzają hostowanie aplikacji w ramach procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="8cb7a-113">Programy obsługi protokołu.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-113">Protocol handlers.</span></span> <span data-ttu-id="8cb7a-114">Składniki związane z protokołem, które są uruchamiane w procesie roboczym i zarządzania komunikacją między procesu roboczego i kart odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="8cb7a-115">Istnieją dwa typy obsługi protokołu: procesu obsługi protokołu i programy obsługi protokołu obiektu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="8cb7a-116">Gdy WAS aktywuje wystąpienia procesu roboczego ładuje obsługi protokołu procesu, które są wymagane do procesu roboczego i używa Menedżera aplikacji, aby utworzyć domenę aplikacji do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="8cb7a-117">Domeny aplikacji, ładuje kod aplikacji, a także obsługi protokołu domeny aplikacji, które protokoły sieciowe używane przez wymagają aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="8cb7a-118">![Architektura WAS](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="8cb7a-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="8cb7a-119">Odbiornik kart</span><span class="sxs-lookup"><span data-stu-id="8cb7a-119">Listener Adapters</span></span>  
 <span data-ttu-id="8cb7a-120">Odbiornik karty są poszczególnych usług Windows, które implementują logikę komunikacji sieciowej używaną do odbierania komunikatów za pomocą protokołu sieciowego, na którym się one nasłuchiwanie.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="8cb7a-121">W poniższej tabeli wymieniono kart odbiornika protokołu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8cb7a-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="8cb7a-122">Nazwa usługi karty odbiornika</span><span class="sxs-lookup"><span data-stu-id="8cb7a-122">Listener adapter service name</span></span>|<span data-ttu-id="8cb7a-123">Protokół</span><span class="sxs-lookup"><span data-stu-id="8cb7a-123">Protocol</span></span>|<span data-ttu-id="8cb7a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cb7a-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="8cb7a-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="8cb7a-125">W3SVC</span></span>|<span data-ttu-id="8cb7a-126">http</span><span class="sxs-lookup"><span data-stu-id="8cb7a-126">http</span></span>|<span data-ttu-id="8cb7a-127">Typowe składnik, który zapewnia Aktywacja HTTP dla usług IIS 7.0 i WCF.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="8cb7a-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="8cb7a-128">NetTcpActivator</span></span>|<span data-ttu-id="8cb7a-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="8cb7a-129">net.tcp</span></span>|<span data-ttu-id="8cb7a-130">Zależy od usługi NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="8cb7a-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="8cb7a-131">NetPipeActivator</span></span>|<span data-ttu-id="8cb7a-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="8cb7a-132">net.pipe</span></span>||  
|<span data-ttu-id="8cb7a-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="8cb7a-133">NetMsmqActivator</span></span>|<span data-ttu-id="8cb7a-134">NET.MSMQ</span><span class="sxs-lookup"><span data-stu-id="8cb7a-134">net.msmq</span></span>|<span data-ttu-id="8cb7a-135">Do użytku z aplikacjami usługi WCF na podstawie usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="8cb7a-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="8cb7a-136">NetMsmqActivator</span></span>|<span data-ttu-id="8cb7a-137">MSMQ.formatname</span><span class="sxs-lookup"><span data-stu-id="8cb7a-137">msmq.formatname</span></span>|<span data-ttu-id="8cb7a-138">Udostępnia wstecznej zgodności z istniejącymi aplikacjami usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="8cb7a-139">Karty odbiornika dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost.config, jak pokazano w poniższym przykładzie XML.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="8cb7a-140">Programy obsługi protokołu</span><span class="sxs-lookup"><span data-stu-id="8cb7a-140">Protocol Handlers</span></span>  
 <span data-ttu-id="8cb7a-141">Proces i obsługi protokołu AppDomain dla określonych protokołów są rejestrowane w pliku Web.config poziomie komputera.</span><span class="sxs-lookup"><span data-stu-id="8cb7a-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8cb7a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cb7a-142">See Also</span></span>  
 [<span data-ttu-id="8cb7a-143">Konfigurowanie usługi WAS do użycia z programem WCF</span><span class="sxs-lookup"><span data-stu-id="8cb7a-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="8cb7a-144">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="8cb7a-144">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
