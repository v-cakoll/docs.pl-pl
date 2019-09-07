---
title: <connectionPoolSettings> dla <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398095"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="c2c41-102">\<connectionPoolSettings > \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="c2c41-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="c2c41-103">Określa dodatkowe ustawienia puli połączeń dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="c2c41-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
<span data-ttu-id="c2c41-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2c41-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2c41-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c2c41-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c2c41-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c2c41-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c2c41-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="c2c41-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="c2c41-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="c2c41-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c2c41-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tcpTransport >** ](tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="c2c41-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)</span></span>\
<span data-ttu-id="c2c41-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="c2c41-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c41-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2c41-111">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2c41-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2c41-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c2c41-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2c41-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2c41-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2c41-114">Attributes</span></span>  
  
|<span data-ttu-id="c2c41-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2c41-115">Attribute</span></span>|<span data-ttu-id="c2c41-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c2c41-116">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="c2c41-117">Ciąg określający nazwę puli połączeń używanej dla kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="c2c41-117">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="c2c41-118">W trybie przesyłania strumieniowego połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c2c41-118">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="c2c41-119">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="c2c41-119">The default is a "default" string.</span></span> <span data-ttu-id="c2c41-120">Możesz zmodyfikować tę wartość, aby wyizolować połączenia dla określonego klienta w oddzielnych grupach.</span><span class="sxs-lookup"><span data-stu-id="c2c41-120">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="c2c41-121">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności połączenia przed jego rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="c2c41-121">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="c2c41-122">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="c2c41-122">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="c2c41-123">A <xref:System.TimeSpan> , który określa czas, po którym zamknięte jest aktywne połączenie.</span><span class="sxs-lookup"><span data-stu-id="c2c41-123">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="c2c41-124">Wartość domyślna to 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="c2c41-124">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="c2c41-125">Połączenie jest zamykane, gdy zostało zwrócone do pamięci podręcznej połączenia, a nie podczas aktywnej transmisji.</span><span class="sxs-lookup"><span data-stu-id="c2c41-125">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="c2c41-126">Pamięć podręczna połączeń używana przez transport TCP tworzy nowe połączenia zgodnie z wymaganiami dla każdego punktu końcowego, do limitu pamięci podręcznej, który jest ustawiony przez`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="c2c41-126">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="c2c41-127">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń ze zdalnym punktem końcowym inicjowanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="c2c41-127">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="c2c41-128">Połączenia przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="c2c41-128">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="c2c41-129">`idleTimeout` Ogranicza czas, w którym połączenia pozostają w kolejce przed zgłoszeniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c2c41-129">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="c2c41-130">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="c2c41-130">The default is 10.</span></span><br /><br /> <span data-ttu-id="c2c41-131">Ten atrybut ogranicza liczbę jednoczesnych aktywnych połączeń z klienta do określonego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="c2c41-131">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="c2c41-132">W przypadku przekroczenia tej wartości przy użyciu większej liczby aktywnych połączeń z klientem usługa może nie odpowiadać na klienta.</span><span class="sxs-lookup"><span data-stu-id="c2c41-132">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="c2c41-133">W takim przypadku ta wartość powinna zostać zmieniona, aby przekroczyć maksymalną dozwoloną liczbę równoczesnych połączeń klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c2c41-133">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2c41-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2c41-134">Child Elements</span></span>  
 <span data-ttu-id="c2c41-135">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2c41-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2c41-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2c41-136">Parent Elements</span></span>  
  
|<span data-ttu-id="c2c41-137">Element</span><span class="sxs-lookup"><span data-stu-id="c2c41-137">Element</span></span>|<span data-ttu-id="c2c41-138">Opis</span><span class="sxs-lookup"><span data-stu-id="c2c41-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2c41-139">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c2c41-139">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="c2c41-140">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="c2c41-140">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2c41-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2c41-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c2c41-142">Transporty</span><span class="sxs-lookup"><span data-stu-id="c2c41-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="c2c41-143">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="c2c41-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c2c41-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c2c41-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c2c41-145">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c2c41-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c2c41-146">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c2c41-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c2c41-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c2c41-147">\<customBinding></span></span>](custombinding.md)
