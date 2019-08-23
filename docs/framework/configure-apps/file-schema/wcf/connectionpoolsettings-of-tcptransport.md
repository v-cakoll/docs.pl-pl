---
title: <connectionPoolSettings> dla <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 787b50296b7ed4f6fdceef244a99dffffae63c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919401"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="47b6c-102">\<connectionPoolSettings > \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="47b6c-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="47b6c-103">Określa dodatkowe ustawienia puli połączeń dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="47b6c-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="47b6c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="47b6c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="47b6c-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="47b6c-105">\<bindings></span></span>  
<span data-ttu-id="47b6c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="47b6c-106">\<customBinding></span></span>  
<span data-ttu-id="47b6c-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="47b6c-107">\<binding></span></span>  
<span data-ttu-id="47b6c-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="47b6c-108">\<tcpTransport></span></span>  
<span data-ttu-id="47b6c-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="47b6c-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b6c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="47b6c-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47b6c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47b6c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="47b6c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47b6c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47b6c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47b6c-113">Attributes</span></span>  
  
|<span data-ttu-id="47b6c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47b6c-114">Attribute</span></span>|<span data-ttu-id="47b6c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="47b6c-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="47b6c-116">Ciąg określający nazwę puli połączeń używanej dla kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="47b6c-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="47b6c-117">W trybie przesyłania strumieniowego połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="47b6c-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="47b6c-118">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="47b6c-118">The default is a "default" string.</span></span> <span data-ttu-id="47b6c-119">Możesz zmodyfikować tę wartość, aby wyizolować połączenia dla określonego klienta w oddzielnych grupach.</span><span class="sxs-lookup"><span data-stu-id="47b6c-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="47b6c-120">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności połączenia przed jego rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="47b6c-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="47b6c-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="47b6c-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="47b6c-122">A <xref:System.TimeSpan> , który określa czas, po którym zamknięte jest aktywne połączenie.</span><span class="sxs-lookup"><span data-stu-id="47b6c-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="47b6c-123">Wartość domyślna to 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="47b6c-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="47b6c-124">Połączenie jest zamykane, gdy zostało zwrócone do pamięci podręcznej połączenia, a nie podczas aktywnej transmisji.</span><span class="sxs-lookup"><span data-stu-id="47b6c-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="47b6c-125">Pamięć podręczna połączeń używana przez transport TCP tworzy nowe połączenia zgodnie z wymaganiami dla każdego punktu końcowego, do limitu pamięci podręcznej, który jest ustawiony przez`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="47b6c-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="47b6c-126">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń ze zdalnym punktem końcowym inicjowanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="47b6c-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="47b6c-127">Połączenia przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="47b6c-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="47b6c-128">`idleTimeout` Ogranicza czas, w którym połączenia pozostają w kolejce przed zgłoszeniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="47b6c-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="47b6c-129">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="47b6c-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="47b6c-130">Ten atrybut ogranicza liczbę jednoczesnych aktywnych połączeń z klienta do określonego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="47b6c-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="47b6c-131">W przypadku przekroczenia tej wartości przy użyciu większej liczby aktywnych połączeń z klientem usługa może nie odpowiadać na klienta.</span><span class="sxs-lookup"><span data-stu-id="47b6c-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="47b6c-132">W takim przypadku ta wartość powinna zostać zmieniona, aby przekroczyć maksymalną dozwoloną liczbę równoczesnych połączeń klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="47b6c-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47b6c-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47b6c-133">Child Elements</span></span>  
 <span data-ttu-id="47b6c-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="47b6c-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47b6c-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47b6c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="47b6c-136">Element</span><span class="sxs-lookup"><span data-stu-id="47b6c-136">Element</span></span>|<span data-ttu-id="47b6c-137">Opis</span><span class="sxs-lookup"><span data-stu-id="47b6c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47b6c-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="47b6c-138">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="47b6c-139">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="47b6c-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47b6c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47b6c-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="47b6c-141">Transporty</span><span class="sxs-lookup"><span data-stu-id="47b6c-141">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="47b6c-142">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="47b6c-142">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="47b6c-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="47b6c-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="47b6c-144">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="47b6c-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="47b6c-145">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="47b6c-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="47b6c-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="47b6c-146">\<customBinding></span></span>](custombinding.md)
