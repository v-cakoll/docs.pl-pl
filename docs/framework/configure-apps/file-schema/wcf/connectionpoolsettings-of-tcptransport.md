---
title: <connectionPoolSettings> dla <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673241"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="52a40-102">\<connectionPoolSettings> of \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="52a40-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="52a40-103">Określa ustawienia puli dodatkowego połączenia dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="52a40-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="52a40-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52a40-104">\<system.serviceModel></span></span>  
<span data-ttu-id="52a40-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="52a40-105">\<bindings></span></span>  
<span data-ttu-id="52a40-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="52a40-106">\<customBinding></span></span>  
<span data-ttu-id="52a40-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="52a40-107">\<binding></span></span>  
<span data-ttu-id="52a40-108">\<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="52a40-108">\<tcpTransport></span></span>  
<span data-ttu-id="52a40-109">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="52a40-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a40-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="52a40-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52a40-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52a40-111">Attributes and Elements</span></span>  
 <span data-ttu-id="52a40-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="52a40-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52a40-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52a40-113">Attributes</span></span>  
  
|<span data-ttu-id="52a40-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="52a40-114">Attribute</span></span>|<span data-ttu-id="52a40-115">Opis</span><span class="sxs-lookup"><span data-stu-id="52a40-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="52a40-116">Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów.</span><span class="sxs-lookup"><span data-stu-id="52a40-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="52a40-117">W trybie przesyłane strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="52a40-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="52a40-118">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="52a40-118">The default is a "default" string.</span></span> <span data-ttu-id="52a40-119">Możesz zmodyfikować tę wartość, aby odizolować połączeń dla konkretnego klienta do osobnych grup.</span><span class="sxs-lookup"><span data-stu-id="52a40-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="52a40-120">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas połączenia może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="52a40-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="52a40-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="52a40-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="52a40-122">Element <xref:System.TimeSpan> , który określa czas, po którym aktywne połączenie jest zamknięte.</span><span class="sxs-lookup"><span data-stu-id="52a40-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="52a40-123">Wartość domyślna to 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="52a40-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="52a40-124">Połączenie zostało zamknięte po został zwrócony z pamięcią podręczną w połączeń, a nie podczas transmisji active.</span><span class="sxs-lookup"><span data-stu-id="52a40-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="52a40-125">Pamięć podręczna połączenia używane przez warstwy transportowej TCP tworzy nowe połączenia, zgodnie z wymaganiami dla każdego punktu końcowego do limitu pamięci podręcznej, która została ustawiona przez `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="52a40-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="52a40-126">Dodatnia liczba całkowita, określająca maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="52a40-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="52a40-127">Połączeń poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="52a40-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="52a40-128">`idleTimeout` Ogranicza okres, w którym pozostają w kolejce zanim zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="52a40-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="52a40-129">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="52a40-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="52a40-130">Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do endpoint określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="52a40-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="52a40-131">Jeśli ta wartość zostanie przekroczony zlecając aktywnych połączeń klienta, usługa może pojawić się odpowiadać do klienta.</span><span class="sxs-lookup"><span data-stu-id="52a40-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="52a40-132">W takim przypadku można dostosować tę wartość w przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="52a40-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52a40-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52a40-133">Child Elements</span></span>  
 <span data-ttu-id="52a40-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="52a40-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52a40-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52a40-135">Parent Elements</span></span>  
  
|<span data-ttu-id="52a40-136">Element</span><span class="sxs-lookup"><span data-stu-id="52a40-136">Element</span></span>|<span data-ttu-id="52a40-137">Opis</span><span class="sxs-lookup"><span data-stu-id="52a40-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52a40-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="52a40-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="52a40-139">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="52a40-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52a40-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52a40-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="52a40-141">Transporty</span><span class="sxs-lookup"><span data-stu-id="52a40-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="52a40-142">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="52a40-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="52a40-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="52a40-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="52a40-144">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="52a40-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="52a40-145">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="52a40-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="52a40-146">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="52a40-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
