---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e5f1d49e0e3bb5f52c5e18577d556d25539434a9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400164"
---
# <a name="namedpipetransport"></a><span data-ttu-id="b5121-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="b5121-101">\<namedPipeTransport></span></span>
<span data-ttu-id="b5121-102">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków, gdy zostanie uwzględniony w niestandardowym powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="b5121-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="b5121-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b5121-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5121-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b5121-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b5121-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b5121-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b5121-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b5121-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b5121-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="b5121-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b5121-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedPipeTransport >**</span><span class="sxs-lookup"><span data-stu-id="b5121-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5121-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5121-109">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5121-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5121-110">Attributes and Elements</span></span>  
<span data-ttu-id="b5121-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5121-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5121-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5121-112">Attributes</span></span>  
<span data-ttu-id="b5121-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="b5121-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5121-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5121-114">Child Elements</span></span>  
  
|<span data-ttu-id="b5121-115">Element</span><span class="sxs-lookup"><span data-stu-id="b5121-115">Element</span></span>|<span data-ttu-id="b5121-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b5121-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5121-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="b5121-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="b5121-118">Pobiera lub ustawia wartość <xref:System.TimeSpan> określającą maksymalny czas, przez który kanał może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="b5121-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="b5121-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="b5121-119">ConnectionBufferSize</span></span>|<span data-ttu-id="b5121-120">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu serializowanego komunikatu w locie z klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="b5121-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="b5121-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="b5121-121">hostNameComparisonMode</span></span>|<span data-ttu-id="b5121-122">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="b5121-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="b5121-123">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="b5121-123">manualAddressing</span></span>|<span data-ttu-id="b5121-124">Pobiera lub ustawia wartość wskazującą, czy ręczne adresowanie wiadomości jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="b5121-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="b5121-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="b5121-125">maxBufferPoolSize</span></span>|<span data-ttu-id="b5121-126">Pobiera lub ustawia maksymalny rozmiar (w bajtach) wszystkich pul buforów używanych przez transport.</span><span class="sxs-lookup"><span data-stu-id="b5121-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="b5121-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="b5121-127">maxBufferSize</span></span>|<span data-ttu-id="b5121-128">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="b5121-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="b5121-129">W przypadku komunikatów przesyłanych strumieniowo ta wartość powinna mieć co najmniej maksymalny możliwy rozmiar nagłówków komunikatów, które są odczytywane w trybie buforowanym.</span><span class="sxs-lookup"><span data-stu-id="b5121-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="b5121-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="b5121-130">maxOutputDelay</span></span>|<span data-ttu-id="b5121-131">Pobiera lub ustawia maksymalny przedział czasu, przez który fragment komunikatu lub pełny komunikat może pozostawać w pamięci przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="b5121-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="b5121-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="b5121-132">maxPendingAccepts</span></span>|<span data-ttu-id="b5121-133">Pobiera lub ustawia maksymalną liczbę kanałów, jaką usługa może oczekiwać na odbiorniku do przetwarzania połączeń przychodzących do usługi.</span><span class="sxs-lookup"><span data-stu-id="b5121-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="b5121-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="b5121-134">maxPendingConnections</span></span>|<span data-ttu-id="b5121-135">Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="b5121-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="b5121-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="b5121-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="b5121-137">Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości (w bajtach), która może zostać odebrana.</span><span class="sxs-lookup"><span data-stu-id="b5121-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="b5121-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="b5121-138">transferMode</span></span>|<span data-ttu-id="b5121-139">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy przesyłane strumieniowo przy użyciu transportu zorientowanego na połączenia.</span><span class="sxs-lookup"><span data-stu-id="b5121-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="b5121-140">\<connectionPoolSettings > \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="b5121-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="b5121-141">Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="b5121-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5121-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5121-142">Parent Elements</span></span>  
  
|<span data-ttu-id="b5121-143">Element</span><span class="sxs-lookup"><span data-stu-id="b5121-143">Element</span></span>|<span data-ttu-id="b5121-144">Opis</span><span class="sxs-lookup"><span data-stu-id="b5121-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5121-145">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b5121-145">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b5121-146">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5121-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5121-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5121-147">Remarks</span></span>  
<span data-ttu-id="b5121-148">Ten transport używa identyfikatorów URI w postaci "net. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="b5121-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="b5121-149">Inne składniki URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b5121-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="b5121-150">`namedPipeTransport` Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="b5121-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="b5121-151">Ten transport jest używany w przypadku komunikacji między maszynami Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b5121-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5121-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5121-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b5121-153">Transporty</span><span class="sxs-lookup"><span data-stu-id="b5121-153">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="b5121-154">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="b5121-154">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="b5121-155">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b5121-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b5121-156">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b5121-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b5121-157">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b5121-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b5121-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b5121-158">\<customBinding></span></span>](custombinding.md)
