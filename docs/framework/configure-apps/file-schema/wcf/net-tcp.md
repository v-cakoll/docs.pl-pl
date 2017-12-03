---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a63d32cc4c0e48b8d3fb40526d810e2f66089d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltnettcpgt"></a><span data-ttu-id="d9538-102">&lt;NET.TCP&gt;</span><span class="sxs-lookup"><span data-stu-id="d9538-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="d9538-103">Określa ustawienia konfiguracji sieci. TCP Port usługi udostępniania, dzięki czemu wielu procesom współużytkowanie tego samego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="d9538-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="d9538-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d9538-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="d9538-105">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="d9538-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9538-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9538-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="d9538-107">Typ</span><span class="sxs-lookup"><span data-stu-id="d9538-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9538-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d9538-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9538-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d9538-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9538-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d9538-110">Attributes</span></span>  
  
|<span data-ttu-id="d9538-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d9538-111">Attribute</span></span>|<span data-ttu-id="d9538-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d9538-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="d9538-113">Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale jeszcze nie są wysyłane do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="d9538-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="d9538-114">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="d9538-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="d9538-115">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków na punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="d9538-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="d9538-116">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="d9538-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="d9538-117">Maksymalna liczba połączeń odbiornika może mieć oczekuje na zatwierdzenie przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d9538-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="d9538-118">Po przekroczeniu tej wartości limitu przydziału nowych połączeń przychodzących są usuwane, a nie oczekuje na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="d9538-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="d9538-119">Połączenie funkcji, takich jak zabezpieczenia wiadomości może spowodować klienta otworzyć więcej niż jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="d9538-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="d9538-120">Administratorzy usługi należy uwzględnić te dodatkowe połączenia podczas ustawiania tej wartości limitu przydziału.</span><span class="sxs-lookup"><span data-stu-id="d9538-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="d9538-121">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="d9538-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d9538-122">A `TimeSpan` , który określa limit czasu dla odczytu danych z ramek i wykonania przekazania połączenia z połączeń podkreślonych.</span><span class="sxs-lookup"><span data-stu-id="d9538-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="d9538-123">Wartość domyślna to "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="d9538-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="d9538-124">Wartość logiczna, która wskazuje, czy port udostępnianej usługi używa usługi Microsoft Teredo do nasłuchiwania protokołu TCP porty zastępczy [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="d9538-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="d9538-125">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="d9538-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9538-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d9538-126">Child Elements</span></span>  
  
|<span data-ttu-id="d9538-127">Element</span><span class="sxs-lookup"><span data-stu-id="d9538-127">Element</span></span>|<span data-ttu-id="d9538-128">Opis</span><span class="sxs-lookup"><span data-stu-id="d9538-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9538-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="d9538-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="d9538-130">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="d9538-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9538-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d9538-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d9538-132">Element</span><span class="sxs-lookup"><span data-stu-id="d9538-132">Element</span></span>|<span data-ttu-id="d9538-133">Opis</span><span class="sxs-lookup"><span data-stu-id="d9538-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9538-134">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d9538-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="d9538-135">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="d9538-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9538-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9538-136">Remarks</span></span>  
 <span data-ttu-id="d9538-137">Aby uzyskać więcej informacji na temat udostępniania portów, zobacz [udostępniania portów Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="d9538-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="d9538-138">Aby poznać sposób konfigurowania usługi współużytkowania portów, zobacz [Konfigurowanie usługi udostępniania portów Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="d9538-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9538-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9538-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="d9538-140">Udostępniania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d9538-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="d9538-141">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d9538-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
