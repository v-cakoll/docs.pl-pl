---
title: Architektura aktywacji WAS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3ecd0ab8e285ff8c05ad8b39f68e5b2d0a3c7886
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="was-activation-architecture"></a><span data-ttu-id="6b00e-102">Architektura aktywacji WAS</span><span class="sxs-lookup"><span data-stu-id="6b00e-102">WAS Activation Architecture</span></span>
<span data-ttu-id="6b00e-103">W tym temacie itemizes i zawiera omówienie składników usługi Windows Process Activation Service (znanej także jako Usługa WAS).</span><span class="sxs-lookup"><span data-stu-id="6b00e-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="6b00e-104">Składniki aktywacji</span><span class="sxs-lookup"><span data-stu-id="6b00e-104">Activation Components</span></span>  
 <span data-ttu-id="6b00e-105">ZOSTAŁ składa się z kilku architektury składników:</span><span class="sxs-lookup"><span data-stu-id="6b00e-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="6b00e-106">Karta odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6b00e-106">Listener adapters.</span></span> <span data-ttu-id="6b00e-107">Usługi systemu Windows, które odbierania komunikatów od określonych protokołów sieciowych i komunikować się z WAS do kierowania wiadomości przychodzących do procesu roboczego poprawne.</span><span class="sxs-lookup"><span data-stu-id="6b00e-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="6b00e-108">ZOSTAŁ.</span><span class="sxs-lookup"><span data-stu-id="6b00e-108">WAS.</span></span> <span data-ttu-id="6b00e-109">Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.</span><span class="sxs-lookup"><span data-stu-id="6b00e-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="6b00e-110">Wykonywalnego procesu roboczego ogólnego (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="6b00e-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="6b00e-111">Menedżer aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b00e-111">Application manager.</span></span> <span data-ttu-id="6b00e-112">Zarządza tworzeniem i okresem istnienia domeny aplikacji, które przetwarzają hosta aplikacji w obrębie elementu roboczego.</span><span class="sxs-lookup"><span data-stu-id="6b00e-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="6b00e-113">Programy obsługi protokołu.</span><span class="sxs-lookup"><span data-stu-id="6b00e-113">Protocol handlers.</span></span> <span data-ttu-id="6b00e-114">Oparte na protokole składniki, których są uruchamiane w procesie roboczym i zarządzania komunikacją między proces roboczy i odbiornika poszczególnych kart.</span><span class="sxs-lookup"><span data-stu-id="6b00e-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="6b00e-115">Istnieją dwa typy programów obsługi protokołu: przetworzyć obsług protokołu i programy obsługi protokołu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b00e-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="6b00e-116">Gdy WAS aktywuje wystąpieniem proces roboczy ładuje obsług protokołu procesu, które są wymagane do procesu roboczego i używa Menedżera aplikacji do tworzenia domeny aplikacji w celu hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b00e-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="6b00e-117">Domeny aplikacji ładuje kodu aplikacji, a także obsługi protokołu domeny aplikacji, które protokoły sieciowe używane przez wymagana.</span><span class="sxs-lookup"><span data-stu-id="6b00e-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="6b00e-118">![Architektura została](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="6b00e-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="6b00e-119">Odbiornik kart</span><span class="sxs-lookup"><span data-stu-id="6b00e-119">Listener Adapters</span></span>  
 <span data-ttu-id="6b00e-120">Odbiornik karty są poszczególnych usług systemu Windows, które implementują logikę komunikacji sieciowej używany do odbierania wiadomości za pomocą protokołu sieciowego, na którym one nasłuchiwanie.</span><span class="sxs-lookup"><span data-stu-id="6b00e-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="6b00e-121">W poniższej tabeli wymieniono karty odbiornika dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokołów.</span><span class="sxs-lookup"><span data-stu-id="6b00e-121">The following table lists the listener adapters for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocols.</span></span>  
  
|<span data-ttu-id="6b00e-122">Nazwa usługi adapter odbiornika</span><span class="sxs-lookup"><span data-stu-id="6b00e-122">Listener adapter service name</span></span>|<span data-ttu-id="6b00e-123">Protokół</span><span class="sxs-lookup"><span data-stu-id="6b00e-123">Protocol</span></span>|<span data-ttu-id="6b00e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b00e-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="6b00e-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="6b00e-125">W3SVC</span></span>|<span data-ttu-id="6b00e-126">Http</span><span class="sxs-lookup"><span data-stu-id="6b00e-126">http</span></span>|<span data-ttu-id="6b00e-127">Typowe składnik Aktywacja HTTP dla obu usług IIS 7.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b00e-127">Common component that provides HTTP activation for both IIS 7.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>|  
|<span data-ttu-id="6b00e-128">Usługi NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="6b00e-128">NetTcpActivator</span></span>|<span data-ttu-id="6b00e-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="6b00e-129">net.tcp</span></span>|<span data-ttu-id="6b00e-130">Zależy od usługi NetTcpPortSharing usługi.</span><span class="sxs-lookup"><span data-stu-id="6b00e-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="6b00e-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="6b00e-131">NetPipeActivator</span></span>|<span data-ttu-id="6b00e-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="6b00e-132">net.pipe</span></span>||  
|<span data-ttu-id="6b00e-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="6b00e-133">NetMsmqActivator</span></span>|<span data-ttu-id="6b00e-134">NET.MSMQ</span><span class="sxs-lookup"><span data-stu-id="6b00e-134">net.msmq</span></span>|<span data-ttu-id="6b00e-135">Do użytku z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]— aplikacje usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6b00e-135">For use with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="6b00e-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="6b00e-136">NetMsmqActivator</span></span>|<span data-ttu-id="6b00e-137">MSMQ.formatname</span><span class="sxs-lookup"><span data-stu-id="6b00e-137">msmq.formatname</span></span>|<span data-ttu-id="6b00e-138">Udostępnia zapewnienia zgodności z istniejącymi aplikacjami usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6b00e-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="6b00e-139">Adaptery odbiornika dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost.config, jak pokazano w poniższym przykładzie XML.</span><span class="sxs-lookup"><span data-stu-id="6b00e-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="6b00e-140">Programy obsługi protokołu</span><span class="sxs-lookup"><span data-stu-id="6b00e-140">Protocol Handlers</span></span>  
 <span data-ttu-id="6b00e-141">Proces i obsługi protokołu domeny aplikacji określonych protokołów są rejestrowane w pliku Web.config poziom maszyny.</span><span class="sxs-lookup"><span data-stu-id="6b00e-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b00e-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b00e-142">See Also</span></span>  
 [<span data-ttu-id="6b00e-143">Konfigurowanie usługi WAS do użycia z programem WCF</span><span class="sxs-lookup"><span data-stu-id="6b00e-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="6b00e-144">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="6b00e-144">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
