---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 63cef2b85aa57b5c1c0e0add1794ebedc73d96c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933050"
---
# <a name="nettcp"></a><span data-ttu-id="ca63e-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="ca63e-102">\<net.tcp></span></span>
<span data-ttu-id="ca63e-103">Określa ustawienia konfiguracji dla sieci. Usługa udostępniania portów TCP, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="ca63e-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="ca63e-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca63e-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ca63e-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="ca63e-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca63e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca63e-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ca63e-107">Typ</span><span class="sxs-lookup"><span data-stu-id="ca63e-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca63e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca63e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca63e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca63e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca63e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca63e-110">Attributes</span></span>  
  
|<span data-ttu-id="ca63e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca63e-111">Attribute</span></span>|<span data-ttu-id="ca63e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ca63e-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="ca63e-113">Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale nie są jeszcze wysyłane do usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ca63e-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="ca63e-114">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="ca63e-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="ca63e-115">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="ca63e-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="ca63e-116">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="ca63e-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="ca63e-117">Maksymalna liczba połączeń, które odbiornik może oczekiwać na akceptację przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ca63e-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="ca63e-118">Po przekroczeniu tej wartości przydziału nowe połączenia przychodzące są usuwane, a nie czekają na ich zaakceptowanie.</span><span class="sxs-lookup"><span data-stu-id="ca63e-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="ca63e-119">Funkcje połączeń, takie jak zabezpieczenia komunikatów, mogą spowodować otwarcie więcej niż jednego połączenia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ca63e-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="ca63e-120">Administratorzy usługi powinni uwzględnić te dodatkowe połączenia podczas ustawiania wartości tego przydziału.</span><span class="sxs-lookup"><span data-stu-id="ca63e-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="ca63e-121">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="ca63e-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ca63e-122">Wartość <xref:System.TimeSpan> określająca limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń.</span><span class="sxs-lookup"><span data-stu-id="ca63e-122">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="ca63e-123">Wartość domyślna to "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="ca63e-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="ca63e-124">Wartość logiczna wskazująca, czy usługa udostępniania portów używa usługi Microsoft Teredo do nasłuchiwania na portach TCP w imieniu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="ca63e-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="ca63e-125">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ca63e-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca63e-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca63e-126">Child Elements</span></span>  
  
|<span data-ttu-id="ca63e-127">Element</span><span class="sxs-lookup"><span data-stu-id="ca63e-127">Element</span></span>|<span data-ttu-id="ca63e-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ca63e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca63e-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="ca63e-129">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="ca63e-130">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="ca63e-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca63e-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca63e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ca63e-132">Element</span><span class="sxs-lookup"><span data-stu-id="ca63e-132">Element</span></span>|<span data-ttu-id="ca63e-133">Opis</span><span class="sxs-lookup"><span data-stu-id="ca63e-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca63e-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca63e-134">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="ca63e-135">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="ca63e-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca63e-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca63e-136">Remarks</span></span>  
 <span data-ttu-id="ca63e-137">Aby uzyskać więcej informacji na temat udostępniania portów, zobacz [net. TCP — Udostępnianie portów](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="ca63e-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="ca63e-138">Aby dowiedzieć się, jak skonfigurować usługę udostępniania portów, zobacz [Konfigurowanie usługi udostępniania portów Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="ca63e-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca63e-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca63e-139">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="ca63e-140">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="ca63e-140">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="ca63e-141">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="ca63e-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
