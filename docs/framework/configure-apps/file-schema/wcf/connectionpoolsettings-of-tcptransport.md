---
title: '&lt;connectionPoolSettings&gt; w &lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 1fbc4e179fa5f59a903dad51728638a1e182b23e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="303e2-102">&lt;connectionPoolSettings&gt; w &lt;tcpTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="303e2-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="303e2-103">Określa ustawienia puli dodatkowego połączenia dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="303e2-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="303e2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="303e2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="303e2-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="303e2-105">\<bindings></span></span>  
<span data-ttu-id="303e2-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="303e2-106">\<customBinding></span></span>  
<span data-ttu-id="303e2-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="303e2-107">\<binding></span></span>  
<span data-ttu-id="303e2-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="303e2-108">\<tcpTransport></span></span>  
<span data-ttu-id="303e2-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="303e2-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="303e2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="303e2-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="303e2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="303e2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="303e2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="303e2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="303e2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="303e2-113">Attributes</span></span>  
  
|<span data-ttu-id="303e2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="303e2-114">Attribute</span></span>|<span data-ttu-id="303e2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="303e2-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="303e2-116">Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów.</span><span class="sxs-lookup"><span data-stu-id="303e2-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="303e2-117">W trybie przesyłanej strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="303e2-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="303e2-118">Wartość domyślna to ciąg "domyślny".</span><span class="sxs-lookup"><span data-stu-id="303e2-118">The default is a "default" string.</span></span> <span data-ttu-id="303e2-119">Można zmodyfikować tę wartość, aby odizolować połączeń dla określonego klienta do oddzielnych grup.</span><span class="sxs-lookup"><span data-stu-id="303e2-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="303e2-120">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas, połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="303e2-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="303e2-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="303e2-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="303e2-122">A <xref:System.TimeSpan> , który określa czas, po którym zamknięte jest aktywne połączenie.</span><span class="sxs-lookup"><span data-stu-id="303e2-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="303e2-123">Wartość domyślna to 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="303e2-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="303e2-124">Połączenie jest zamykane po została zwrócona do pamięci podręcznej połączenia, a nie podczas transmisji aktywne.</span><span class="sxs-lookup"><span data-stu-id="303e2-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="303e2-125">Pamięć podręczna połączenie używane przez transportu TCP tworzy nowe połączenia, co jest wymagane dla każdego punktu końcowego w granicach pamięci podręcznej, który jest uporządkowany według `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="303e2-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="303e2-126">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="303e2-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="303e2-127">Połączenia poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="303e2-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="303e2-128">`idleTimeout` Ogranicza okres, w którym połączenia pozostają w kolejce przed jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="303e2-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="303e2-129">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="303e2-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="303e2-130">Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="303e2-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="303e2-131">Tę wartość po przekroczeniu dzięki użyciu aktywnych połączeń klienckich, usługi mogą być wyświetlane odpowiadać do klienta.</span><span class="sxs-lookup"><span data-stu-id="303e2-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="303e2-132">W takim przypadku ta wartość powinna dostosowana do przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="303e2-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="303e2-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="303e2-133">Child Elements</span></span>  
 <span data-ttu-id="303e2-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="303e2-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="303e2-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="303e2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="303e2-136">Element</span><span class="sxs-lookup"><span data-stu-id="303e2-136">Element</span></span>|<span data-ttu-id="303e2-137">Opis</span><span class="sxs-lookup"><span data-stu-id="303e2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="303e2-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="303e2-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="303e2-139">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="303e2-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="303e2-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="303e2-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="303e2-141">Transporty</span><span class="sxs-lookup"><span data-stu-id="303e2-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="303e2-142">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="303e2-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="303e2-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="303e2-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="303e2-144">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="303e2-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="303e2-145">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="303e2-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="303e2-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="303e2-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
