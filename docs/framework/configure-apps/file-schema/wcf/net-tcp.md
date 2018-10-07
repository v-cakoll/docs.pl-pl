---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: c67aeca183eb476460fa0be2c6dcd9c6077165d8
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842349"
---
# <a name="ltnettcpgt"></a><span data-ttu-id="fb066-102">&lt;net.tcp&gt;</span><span class="sxs-lookup"><span data-stu-id="fb066-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="fb066-103">Określa ustawienia konfiguracji sieci. TCP usługi udostępniania portów, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="fb066-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="fb066-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fb066-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="fb066-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="fb066-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb066-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb066-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="fb066-107">Typ</span><span class="sxs-lookup"><span data-stu-id="fb066-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb066-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb066-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb066-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb066-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb066-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb066-110">Attributes</span></span>  
  
|<span data-ttu-id="fb066-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb066-111">Attribute</span></span>|<span data-ttu-id="fb066-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fb066-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="fb066-113">Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale jeszcze nie są wysyłane do usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fb066-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="fb066-114">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="fb066-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="fb066-115">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków na punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="fb066-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="fb066-116">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="fb066-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="fb066-117">Maksymalna liczba połączeń, które mogą mieć odbiornika, oczekuje na zatwierdzenie przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="fb066-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="fb066-118">Po przekroczeniu tej wartości limitu przydziału na nowe połączenia przychodzące są odrzucane zamiast oczekuje na zatwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="fb066-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="fb066-119">Połączenie funkcji, takich jak zabezpieczenia komunikatów może spowodować klienta otworzyć więcej niż jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="fb066-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="fb066-120">Administratorzy usługi należy uwzględnić w przypadku tych dodatkowych połączeń, podczas ustawiania tej wartości limitu przydziału.</span><span class="sxs-lookup"><span data-stu-id="fb066-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="fb066-121">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="fb066-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fb066-122">Element `TimeSpan` , który określa limit czasu dla odczytu danych z ramek i wykonania przekazania połączenia z połączeń podkreślonych.</span><span class="sxs-lookup"><span data-stu-id="fb066-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="fb066-123">Wartość domyślna to "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="fb066-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="fb066-124">Wartość logiczna wskazująca, czy port udostępnianej usługi używa usługi Microsoft Teredo aby nasłuchiwać portów TCP w imieniu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="fb066-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="fb066-125">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="fb066-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb066-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb066-126">Child Elements</span></span>  
  
|<span data-ttu-id="fb066-127">Element</span><span class="sxs-lookup"><span data-stu-id="fb066-127">Element</span></span>|<span data-ttu-id="fb066-128">Opis</span><span class="sxs-lookup"><span data-stu-id="fb066-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb066-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fb066-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="fb066-130">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="fb066-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb066-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb066-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fb066-132">Element</span><span class="sxs-lookup"><span data-stu-id="fb066-132">Element</span></span>|<span data-ttu-id="fb066-133">Opis</span><span class="sxs-lookup"><span data-stu-id="fb066-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb066-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fb066-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="fb066-135">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="fb066-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb066-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb066-136">Remarks</span></span>  
 <span data-ttu-id="fb066-137">Aby uzyskać więcej informacji na temat współużytkowania portów, zobacz [współużytkowania portów Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="fb066-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="fb066-138">Aby dowiedzieć się, jak skonfigurować port udostępnianej usługi, zobacz [konfigurowania usługi udostępniania portów Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="fb066-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb066-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb066-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="fb066-140">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fb066-140">Net.TCP Port Sharing</span></span>](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="fb066-141">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fb066-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
