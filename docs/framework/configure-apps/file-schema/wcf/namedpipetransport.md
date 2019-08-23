---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933208"
---
# <a name="namedpipetransport"></a><span data-ttu-id="f2304-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="f2304-101">\<namedPipeTransport></span></span>
<span data-ttu-id="f2304-102">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków, gdy zostanie uwzględniony w niestandardowym powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f2304-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="f2304-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2304-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f2304-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="f2304-104">\<bindings></span></span>  
<span data-ttu-id="f2304-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f2304-105">\<customBinding></span></span>  
<span data-ttu-id="f2304-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f2304-106">\<binding></span></span>  
<span data-ttu-id="f2304-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="f2304-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2304-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2304-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2304-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2304-109">Attributes and Elements</span></span>  
<span data-ttu-id="f2304-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f2304-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2304-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2304-111">Attributes</span></span>  
<span data-ttu-id="f2304-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="f2304-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2304-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2304-113">Child Elements</span></span>  
  
|<span data-ttu-id="f2304-114">Element</span><span class="sxs-lookup"><span data-stu-id="f2304-114">Element</span></span>|<span data-ttu-id="f2304-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f2304-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2304-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="f2304-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="f2304-117">Pobiera lub ustawia wartość <xref:System.TimeSpan> określającą maksymalny czas, przez który kanał może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="f2304-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="f2304-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="f2304-118">ConnectionBufferSize</span></span>|<span data-ttu-id="f2304-119">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu serializowanego komunikatu w locie z klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="f2304-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="f2304-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f2304-120">hostNameComparisonMode</span></span>|<span data-ttu-id="f2304-121">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f2304-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="f2304-122">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="f2304-122">manualAddressing</span></span>|<span data-ttu-id="f2304-123">Pobiera lub ustawia wartość wskazującą, czy ręczne adresowanie wiadomości jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="f2304-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="f2304-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f2304-124">maxBufferPoolSize</span></span>|<span data-ttu-id="f2304-125">Pobiera lub ustawia maksymalny rozmiar (w bajtach) wszystkich pul buforów używanych przez transport.</span><span class="sxs-lookup"><span data-stu-id="f2304-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="f2304-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f2304-126">maxBufferSize</span></span>|<span data-ttu-id="f2304-127">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="f2304-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="f2304-128">W przypadku komunikatów przesyłanych strumieniowo ta wartość powinna mieć co najmniej maksymalny możliwy rozmiar nagłówków komunikatów, które są odczytywane w trybie buforowanym.</span><span class="sxs-lookup"><span data-stu-id="f2304-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="f2304-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="f2304-129">maxOutputDelay</span></span>|<span data-ttu-id="f2304-130">Pobiera lub ustawia maksymalny przedział czasu, przez który fragment komunikatu lub pełny komunikat może pozostawać w pamięci przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="f2304-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="f2304-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="f2304-131">maxPendingAccepts</span></span>|<span data-ttu-id="f2304-132">Pobiera lub ustawia maksymalną liczbę kanałów, jaką usługa może oczekiwać na odbiorniku do przetwarzania połączeń przychodzących do usługi.</span><span class="sxs-lookup"><span data-stu-id="f2304-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="f2304-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="f2304-133">maxPendingConnections</span></span>|<span data-ttu-id="f2304-134">Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="f2304-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="f2304-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f2304-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="f2304-136">Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości (w bajtach), która może zostać odebrana.</span><span class="sxs-lookup"><span data-stu-id="f2304-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="f2304-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="f2304-137">transferMode</span></span>|<span data-ttu-id="f2304-138">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy przesyłane strumieniowo przy użyciu transportu zorientowanego na połączenia.</span><span class="sxs-lookup"><span data-stu-id="f2304-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="f2304-139">\<connectionPoolSettings > \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="f2304-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="f2304-140">Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="f2304-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2304-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2304-141">Parent Elements</span></span>  
  
|<span data-ttu-id="f2304-142">Element</span><span class="sxs-lookup"><span data-stu-id="f2304-142">Element</span></span>|<span data-ttu-id="f2304-143">Opis</span><span class="sxs-lookup"><span data-stu-id="f2304-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2304-144">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f2304-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f2304-145">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f2304-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2304-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2304-146">Remarks</span></span>  
<span data-ttu-id="f2304-147">Ten transport używa identyfikatorów URI w postaci "net. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="f2304-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="f2304-148">Inne składniki URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f2304-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="f2304-149">`namedPipeTransport` Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="f2304-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="f2304-150">Ten transport jest używany w przypadku komunikacji między maszynami Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f2304-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2304-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2304-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f2304-152">Transporty</span><span class="sxs-lookup"><span data-stu-id="f2304-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="f2304-153">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="f2304-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="f2304-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f2304-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2304-155">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f2304-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f2304-156">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f2304-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f2304-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f2304-157">\<customBinding></span></span>](custombinding.md)
