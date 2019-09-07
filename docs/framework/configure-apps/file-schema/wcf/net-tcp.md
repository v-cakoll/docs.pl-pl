---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397694"
---
# <a name="nettcp"></a><span data-ttu-id="04358-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="04358-102">\<net.tcp></span></span>
<span data-ttu-id="04358-103">Określa ustawienia konfiguracji dla sieci. Usługa udostępniania portów TCP, która umożliwia wielu procesom współużytkowanie tego samego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="04358-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
<span data-ttu-id="04358-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04358-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04358-105">&nbsp;&nbsp;[ **\<> System. serviceModel. Activation**](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="04358-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="04358-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> net. TCP**</span><span class="sxs-lookup"><span data-stu-id="04358-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04358-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="04358-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="04358-108">Typ</span><span class="sxs-lookup"><span data-stu-id="04358-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04358-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04358-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04358-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04358-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04358-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04358-111">Attributes</span></span>  
  
|<span data-ttu-id="04358-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04358-112">Attribute</span></span>|<span data-ttu-id="04358-113">Opis</span><span class="sxs-lookup"><span data-stu-id="04358-113">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="04358-114">Liczba całkowita określająca maksymalną liczbę oczekujących połączeń, które są akceptowane z udostępnionego połączenia, ale nie są jeszcze wysyłane do usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="04358-114">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="04358-115">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="04358-115">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="04358-116">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="04358-116">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="04358-117">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="04358-117">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="04358-118">Maksymalna liczba połączeń, które odbiornik może oczekiwać na akceptację przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="04358-118">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="04358-119">Po przekroczeniu tej wartości przydziału nowe połączenia przychodzące są usuwane, a nie czekają na ich zaakceptowanie.</span><span class="sxs-lookup"><span data-stu-id="04358-119">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="04358-120">Funkcje połączeń, takie jak zabezpieczenia komunikatów, mogą spowodować otwarcie więcej niż jednego połączenia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="04358-120">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="04358-121">Administratorzy usługi powinni uwzględnić te dodatkowe połączenia podczas ustawiania wartości tego przydziału.</span><span class="sxs-lookup"><span data-stu-id="04358-121">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="04358-122">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="04358-122">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="04358-123">Wartość <xref:System.TimeSpan> określająca limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń.</span><span class="sxs-lookup"><span data-stu-id="04358-123">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="04358-124">Wartość domyślna to "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="04358-124">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="04358-125">Wartość logiczna wskazująca, czy usługa udostępniania portów używa usługi Microsoft Teredo do nasłuchiwania na portach TCP w imieniu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="04358-125">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="04358-126">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="04358-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04358-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04358-127">Child Elements</span></span>  
  
|<span data-ttu-id="04358-128">Element</span><span class="sxs-lookup"><span data-stu-id="04358-128">Element</span></span>|<span data-ttu-id="04358-129">Opis</span><span class="sxs-lookup"><span data-stu-id="04358-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04358-130">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="04358-130">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="04358-131">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="04358-131">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04358-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04358-132">Parent Elements</span></span>  
  
|<span data-ttu-id="04358-133">Element</span><span class="sxs-lookup"><span data-stu-id="04358-133">Element</span></span>|<span data-ttu-id="04358-134">Opis</span><span class="sxs-lookup"><span data-stu-id="04358-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04358-135">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="04358-135">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="04358-136">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="04358-136">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04358-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04358-137">Remarks</span></span>  
 <span data-ttu-id="04358-138">Aby uzyskać więcej informacji na temat udostępniania portów, zobacz [net. TCP — Udostępnianie portów](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="04358-138">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="04358-139">Aby dowiedzieć się, jak skonfigurować usługę udostępniania portów, zobacz [Konfigurowanie usługi udostępniania portów Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="04358-139">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04358-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04358-140">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="04358-141">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="04358-141">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="04358-142">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="04358-142">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
