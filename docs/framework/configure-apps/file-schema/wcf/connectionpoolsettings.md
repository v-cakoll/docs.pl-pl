---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400481"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="62e95-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="62e95-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="62e95-102">Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="62e95-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
<span data-ttu-id="62e95-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62e95-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62e95-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62e95-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62e95-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="62e95-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="62e95-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="62e95-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="62e95-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="62e95-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="62e95-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedPipeTransport >** ](namedpipetransport.md)</span><span class="sxs-lookup"><span data-stu-id="62e95-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)</span></span>\
<span data-ttu-id="62e95-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="62e95-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e95-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e95-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62e95-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62e95-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62e95-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62e95-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62e95-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62e95-113">Attributes</span></span>  
  
|<span data-ttu-id="62e95-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62e95-114">Attribute</span></span>|<span data-ttu-id="62e95-115">Opis</span><span class="sxs-lookup"><span data-stu-id="62e95-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="62e95-116">Ciąg określający nazwę puli połączeń używanej dla kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="62e95-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="62e95-117">W trybie przesyłania strumieniowego połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="62e95-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="62e95-118">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="62e95-118">The default is a "default" string.</span></span> <span data-ttu-id="62e95-119">Możesz zmodyfikować tę wartość, aby wyizolować połączenia dla określonego klienta w oddzielnych grupach.</span><span class="sxs-lookup"><span data-stu-id="62e95-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="62e95-120">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności połączenia przed jego rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="62e95-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="62e95-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="62e95-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="62e95-122">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń ze zdalnym punktem końcowym inicjowanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="62e95-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="62e95-123">Połączenia przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="62e95-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="62e95-124">`idleTimeout` Ogranicza czas, w którym połączenia pozostają w kolejce przed zgłoszeniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="62e95-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="62e95-125">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="62e95-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="62e95-126">Ten atrybut ogranicza liczbę jednoczesnych aktywnych połączeń z klienta do określonego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="62e95-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="62e95-127">W przypadku przekroczenia tej wartości przy użyciu większej liczby aktywnych połączeń z klientem usługa może nie odpowiadać na klienta.</span><span class="sxs-lookup"><span data-stu-id="62e95-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="62e95-128">W takim przypadku ta wartość powinna zostać zmieniona, aby przekroczyć maksymalną dozwoloną liczbę równoczesnych połączeń klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62e95-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62e95-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62e95-129">Child Elements</span></span>  
 <span data-ttu-id="62e95-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="62e95-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62e95-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62e95-131">Parent Elements</span></span>  
  
|<span data-ttu-id="62e95-132">Element</span><span class="sxs-lookup"><span data-stu-id="62e95-132">Element</span></span>|<span data-ttu-id="62e95-133">Opis</span><span class="sxs-lookup"><span data-stu-id="62e95-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62e95-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="62e95-134">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="62e95-135">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="62e95-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62e95-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62e95-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="62e95-137">Transporty</span><span class="sxs-lookup"><span data-stu-id="62e95-137">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="62e95-138">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="62e95-138">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="62e95-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="62e95-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62e95-140">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="62e95-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="62e95-141">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="62e95-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="62e95-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="62e95-142">\<customBinding></span></span>](custombinding.md)
