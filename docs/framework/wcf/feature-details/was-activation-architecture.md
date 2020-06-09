---
title: Architektura aktywacji WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: cfbfd91f9e7bc2e1b4f8485d5ae22c1fb2b5228b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600675"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="6cfcc-102">Architektura aktywacji WAS</span><span class="sxs-lookup"><span data-stu-id="6cfcc-102">WAS Activation Architecture</span></span>
<span data-ttu-id="6cfcc-103">W tym temacie wyszczególniono i omówiono składniki usługi aktywacji procesów systemu Windows (nazywanej także usługą WAS).</span><span class="sxs-lookup"><span data-stu-id="6cfcc-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="6cfcc-104">Składniki aktywacji</span><span class="sxs-lookup"><span data-stu-id="6cfcc-104">Activation Components</span></span>  
 <span data-ttu-id="6cfcc-105">Składa się z kilku składników architektury:</span><span class="sxs-lookup"><span data-stu-id="6cfcc-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="6cfcc-106">Adaptery odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-106">Listener adapters.</span></span> <span data-ttu-id="6cfcc-107">Usługi systemu Windows, które odbierają komunikaty z określonych protokołów sieciowych i komunikują się z usługą, przekierować komunikaty przychodzące do poprawnego procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="6cfcc-108">Błędu.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-108">WAS.</span></span> <span data-ttu-id="6cfcc-109">Usługa systemu Windows, która zarządza tworzeniem i okresem istnienia procesów roboczych.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="6cfcc-110">Plik wykonywalny ogólnego procesu roboczego (w3wp. exe).</span><span class="sxs-lookup"><span data-stu-id="6cfcc-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="6cfcc-111">Menedżer aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-111">Application manager.</span></span> <span data-ttu-id="6cfcc-112">Zarządza tworzeniem i okresem istnienia domen aplikacji, które obsługują aplikacje w ramach procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="6cfcc-113">Procedury obsługi protokołu.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-113">Protocol handlers.</span></span> <span data-ttu-id="6cfcc-114">Składniki specyficzne dla protokołu, które są uruchamiane w procesie roboczym i zarządzają komunikacją między procesem roboczym a poszczególnymi kartami odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="6cfcc-115">Istnieją dwa typy obsługi protokołów: procedury obsługi protokołu przetwarzania i procedury obsługi protokołu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="6cfcc-116">Gdy program został aktywowany wystąpienie procesu roboczego, ładuje do procesu roboczego programy obsługi protokołu procesu, a następnie za pomocą Menedżera aplikacji utworzyć domenę aplikacji do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="6cfcc-117">Domena aplikacji ładuje kod aplikacji, a także obsługę protokołów AppDomain, których wymagają protokoły sieciowe używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Zrzut ekranu przedstawiający architekturę WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="6cfcc-119">Adaptery odbiornika</span><span class="sxs-lookup"><span data-stu-id="6cfcc-119">Listener Adapters</span></span>  
 <span data-ttu-id="6cfcc-120">Adaptery odbiorników to pojedyncze usługi systemu Windows, które implementują logikę komunikacji sieciowej służącą do odbierania komunikatów przy użyciu protokołu sieciowego, na którym nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="6cfcc-121">W poniższej tabeli przedstawiono karty odbiorników dla protokołów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6cfcc-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="6cfcc-122">Nazwa usługi adaptera odbiornika</span><span class="sxs-lookup"><span data-stu-id="6cfcc-122">Listener adapter service name</span></span>|<span data-ttu-id="6cfcc-123">Protokół</span><span class="sxs-lookup"><span data-stu-id="6cfcc-123">Protocol</span></span>|<span data-ttu-id="6cfcc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cfcc-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="6cfcc-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="6cfcc-125">W3SVC</span></span>|<span data-ttu-id="6cfcc-126">http</span><span class="sxs-lookup"><span data-stu-id="6cfcc-126">http</span></span>|<span data-ttu-id="6cfcc-127">Wspólny składnik zapewniający aktywację HTTP dla usług IIS 7,0 i WCF.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="6cfcc-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="6cfcc-128">NetTcpActivator</span></span>|<span data-ttu-id="6cfcc-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="6cfcc-129">net.tcp</span></span>|<span data-ttu-id="6cfcc-130">Zależy od usługi NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="6cfcc-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="6cfcc-131">NetPipeActivator</span></span>|<span data-ttu-id="6cfcc-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="6cfcc-132">net.pipe</span></span>||  
|<span data-ttu-id="6cfcc-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="6cfcc-133">NetMsmqActivator</span></span>|<span data-ttu-id="6cfcc-134">NET. MSMQ</span><span class="sxs-lookup"><span data-stu-id="6cfcc-134">net.msmq</span></span>|<span data-ttu-id="6cfcc-135">Do użytku z aplikacjami usługi kolejkowania komunikatów opartymi na platformie WCF.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="6cfcc-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="6cfcc-136">NetMsmqActivator</span></span>|<span data-ttu-id="6cfcc-137">wartość MSMQ. formatname</span><span class="sxs-lookup"><span data-stu-id="6cfcc-137">msmq.formatname</span></span>|<span data-ttu-id="6cfcc-138">Zapewnia zgodność z poprzednimi wersjami istniejących aplikacji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="6cfcc-139">Adaptery odbiorników dla określonych protokołów są rejestrowane podczas instalacji w pliku applicationHost. config, jak pokazano w poniższym przykładzie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="6cfcc-140">Programy obsługi protokołów</span><span class="sxs-lookup"><span data-stu-id="6cfcc-140">Protocol Handlers</span></span>  
 <span data-ttu-id="6cfcc-141">Procedury obsługi protokołu i programu AppDomain dla określonych protokołów są rejestrowane w pliku Web. config na poziomie komputera.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cfcc-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cfcc-142">See also</span></span>

- [<span data-ttu-id="6cfcc-143">Konfigurowanie usługi WAS do użycia z programem WCF</span><span class="sxs-lookup"><span data-stu-id="6cfcc-143">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="6cfcc-144">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6cfcc-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
