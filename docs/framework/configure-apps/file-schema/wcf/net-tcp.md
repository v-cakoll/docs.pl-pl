---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397694"
---
# \<net.tcp>
<span data-ttu-id="c2287-102">Określa ustawienia konfiguracji dla sieci. Usługa udostępniania portów TCP, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="c2287-102">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="c2287-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2287-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="c2287-104">Typ</span><span class="sxs-lookup"><span data-stu-id="c2287-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2287-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2287-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c2287-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2287-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2287-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2287-107">Attributes</span></span>  
  
|<span data-ttu-id="c2287-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2287-108">Attribute</span></span>|<span data-ttu-id="c2287-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c2287-109">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="c2287-110">Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale nie są jeszcze wysyłane do usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c2287-110">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="c2287-111">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="c2287-111">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="c2287-112">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="c2287-112">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="c2287-113">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="c2287-113">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="c2287-114">Maksymalna liczba połączeń, które odbiornik może oczekiwać na akceptację przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c2287-114">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="c2287-115">Po przekroczeniu tej wartości przydziału nowe połączenia przychodzące są usuwane, a nie czekają na ich zaakceptowanie.</span><span class="sxs-lookup"><span data-stu-id="c2287-115">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="c2287-116">Funkcje połączeń, takie jak zabezpieczenia komunikatów, mogą spowodować otwarcie więcej niż jednego połączenia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c2287-116">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="c2287-117">Administratorzy usługi powinni uwzględnić te dodatkowe połączenia podczas ustawiania wartości tego przydziału.</span><span class="sxs-lookup"><span data-stu-id="c2287-117">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="c2287-118">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="c2287-118">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="c2287-119">Wartość określająca <xref:System.TimeSpan> limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń.</span><span class="sxs-lookup"><span data-stu-id="c2287-119">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="c2287-120">Wartość domyślna to "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="c2287-120">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="c2287-121">Wartość logiczna wskazująca, czy usługa udostępniania portów używa usługi Microsoft Teredo do nasłuchiwania na portach TCP w imieniu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="c2287-121">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="c2287-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c2287-122">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2287-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2287-123">Child Elements</span></span>  
  
|<span data-ttu-id="c2287-124">Element</span><span class="sxs-lookup"><span data-stu-id="c2287-124">Element</span></span>|<span data-ttu-id="c2287-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c2287-125">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="c2287-126">Kolekcja elementów konfiguracji, które zawierają atrybut służący `securityIdentifier` do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="c2287-126">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2287-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2287-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c2287-128">Element</span><span class="sxs-lookup"><span data-stu-id="c2287-128">Element</span></span>|<span data-ttu-id="c2287-129">Opis</span><span class="sxs-lookup"><span data-stu-id="c2287-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="c2287-130">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="c2287-130">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2287-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2287-131">Remarks</span></span>  
 <span data-ttu-id="c2287-132">Aby uzyskać więcej informacji na temat udostępniania portów, zobacz [net. TCP — Udostępnianie portów](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="c2287-132">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="c2287-133">Aby dowiedzieć się, jak skonfigurować usługę udostępniania portów, zobacz [Konfigurowanie usługi udostępniania portów Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="c2287-133">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2287-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2287-134">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="c2287-135">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="c2287-135">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="c2287-136">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="c2287-136">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
