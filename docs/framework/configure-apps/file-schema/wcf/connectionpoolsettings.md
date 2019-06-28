---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 0e56bb5c9e485559d712281a51e79f54c9661b5a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423137"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="c7f7a-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="c7f7a-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="c7f7a-102">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="c7f7a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c7f7a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c7f7a-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c7f7a-104">\<bindings></span></span>  
<span data-ttu-id="c7f7a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c7f7a-105">\<customBinding></span></span>  
<span data-ttu-id="c7f7a-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c7f7a-106">\<binding></span></span>  
<span data-ttu-id="c7f7a-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="c7f7a-107">\<namePipeTransport></span></span>  
<span data-ttu-id="c7f7a-108">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="c7f7a-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f7a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7f7a-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7f7a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7f7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c7f7a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7f7a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7f7a-112">Attributes</span></span>  
  
|<span data-ttu-id="c7f7a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7f7a-113">Attribute</span></span>|<span data-ttu-id="c7f7a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c7f7a-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="c7f7a-115">Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="c7f7a-116">W trybie przesyłane strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="c7f7a-117">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="c7f7a-117">The default is a "default" string.</span></span> <span data-ttu-id="c7f7a-118">Możesz zmodyfikować tę wartość, aby odizolować połączeń dla konkretnego klienta do osobnych grup.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="c7f7a-119">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas połączenia może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="c7f7a-120">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="c7f7a-121">Dodatnia liczba całkowita, określająca maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="c7f7a-122">Połączeń poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="c7f7a-123">`idleTimeout` Ogranicza okres, w którym pozostają w kolejce zanim zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="c7f7a-124">Wartość domyślna wynosi 10.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="c7f7a-125">Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do endpoint określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="c7f7a-126">Jeśli ta wartość zostanie przekroczony zlecając aktywnych połączeń klienta, usługa może pojawić się odpowiadać do klienta.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="c7f7a-127">W takim przypadku można dostosować tę wartość w przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7f7a-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7f7a-128">Child Elements</span></span>  
 <span data-ttu-id="c7f7a-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7f7a-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7f7a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="c7f7a-131">Element</span><span class="sxs-lookup"><span data-stu-id="c7f7a-131">Element</span></span>|<span data-ttu-id="c7f7a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="c7f7a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7f7a-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c7f7a-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="c7f7a-134">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="c7f7a-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7f7a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f7a-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c7f7a-136">Transporty</span><span class="sxs-lookup"><span data-stu-id="c7f7a-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="c7f7a-137">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="c7f7a-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c7f7a-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c7f7a-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c7f7a-139">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c7f7a-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c7f7a-140">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c7f7a-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c7f7a-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c7f7a-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
