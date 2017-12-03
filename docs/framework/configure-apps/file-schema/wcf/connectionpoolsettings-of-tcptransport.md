---
title: '&lt;connectionPoolSettings&gt; w &lt;tcpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b0bd7303f714847228bcd8bfed7134fe9942c1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="ca357-102">&lt;connectionPoolSettings&gt; w &lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="ca357-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="ca357-103">Określa ustawienia puli dodatkowego połączenia dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="ca357-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="ca357-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ca357-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ca357-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ca357-105">\<bindings></span></span>  
<span data-ttu-id="ca357-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ca357-106">\<customBinding></span></span>  
<span data-ttu-id="ca357-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca357-107">\<binding></span></span>  
<span data-ttu-id="ca357-108">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="ca357-108">\<tcpTransport></span></span>  
<span data-ttu-id="ca357-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="ca357-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca357-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca357-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca357-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca357-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca357-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca357-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca357-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca357-113">Attributes</span></span>  
  
|<span data-ttu-id="ca357-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca357-114">Attribute</span></span>|<span data-ttu-id="ca357-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ca357-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="ca357-116">Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów.</span><span class="sxs-lookup"><span data-stu-id="ca357-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="ca357-117">W trybie przesyłanej strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ca357-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="ca357-118">Wartość domyślna to ciąg "domyślny".</span><span class="sxs-lookup"><span data-stu-id="ca357-118">The default is a "default" string.</span></span> <span data-ttu-id="ca357-119">Można zmodyfikować tę wartość, aby odizolować połączeń dla określonego klienta do oddzielnych grup.</span><span class="sxs-lookup"><span data-stu-id="ca357-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="ca357-120">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas, połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="ca357-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="ca357-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="ca357-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="ca357-122">A <xref:System.TimeSpan> , który określa czas, po którym zamknięte jest aktywne połączenie.</span><span class="sxs-lookup"><span data-stu-id="ca357-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="ca357-123">Wartość domyślna to 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="ca357-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="ca357-124">Połączenie jest zamykane po została zwrócona do pamięci podręcznej połączenia, a nie podczas transmisji aktywne.</span><span class="sxs-lookup"><span data-stu-id="ca357-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="ca357-125">Pamięć podręczna połączenie używane przez transportu TCP tworzy nowe połączenia, co jest wymagane dla każdego punktu końcowego w granicach pamięci podręcznej, który jest uporządkowany według`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="ca357-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="ca357-126">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ca357-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="ca357-127">Połączenia poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="ca357-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="ca357-128">`idleTimeout` Ogranicza okres, w którym połączenia pozostają w kolejce przed jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ca357-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="ca357-129">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="ca357-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="ca357-130">Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ca357-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="ca357-131">Tę wartość po przekroczeniu dzięki użyciu aktywnych połączeń klienckich, usługi mogą być wyświetlane odpowiadać do klienta.</span><span class="sxs-lookup"><span data-stu-id="ca357-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="ca357-132">W takim przypadku ta wartość powinna dostosowana do przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ca357-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca357-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca357-133">Child Elements</span></span>  
 <span data-ttu-id="ca357-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca357-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca357-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca357-135">Parent Elements</span></span>  
  
|<span data-ttu-id="ca357-136">Element</span><span class="sxs-lookup"><span data-stu-id="ca357-136">Element</span></span>|<span data-ttu-id="ca357-137">Opis</span><span class="sxs-lookup"><span data-stu-id="ca357-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca357-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="ca357-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="ca357-139">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="ca357-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca357-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca357-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="ca357-141">Transporty</span><span class="sxs-lookup"><span data-stu-id="ca357-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="ca357-142">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="ca357-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="ca357-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ca357-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ca357-144">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ca357-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ca357-145">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ca357-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ca357-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ca357-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
