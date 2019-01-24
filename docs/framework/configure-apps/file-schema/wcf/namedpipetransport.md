---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: cdb2863ff376a92f7c4b679f4812b895ac3f2234
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518842"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="68e72-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="68e72-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="68e72-103">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="68e72-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="68e72-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="68e72-104">\<system.serviceModel></span></span>  
<span data-ttu-id="68e72-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="68e72-105">\<bindings></span></span>  
<span data-ttu-id="68e72-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="68e72-106">\<customBinding></span></span>  
<span data-ttu-id="68e72-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="68e72-107">\<binding></span></span>  
<span data-ttu-id="68e72-108">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="68e72-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e72-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="68e72-109">Syntax</span></span>  
  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68e72-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="68e72-110">Attributes and Elements</span></span>  
<span data-ttu-id="68e72-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="68e72-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68e72-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="68e72-112">Attributes</span></span>  
<span data-ttu-id="68e72-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="68e72-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68e72-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="68e72-114">Child Elements</span></span>  
  
|<span data-ttu-id="68e72-115">Element</span><span class="sxs-lookup"><span data-stu-id="68e72-115">Element</span></span>|<span data-ttu-id="68e72-116">Opis</span><span class="sxs-lookup"><span data-stu-id="68e72-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68e72-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="68e72-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="68e72-118">Pobiera lub ustawia <xref:System.TimeSpan> określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="68e72-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="68e72-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="68e72-119">ConnectionBufferSize</span></span>|<span data-ttu-id="68e72-120">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="68e72-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="68e72-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="68e72-121">hostNameComparisonMode</span></span>|<span data-ttu-id="68e72-122">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="68e72-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="68e72-123">opcję manualAddressing</span><span class="sxs-lookup"><span data-stu-id="68e72-123">manualAddressing</span></span>|<span data-ttu-id="68e72-124">Pobiera lub ustawia wartość wskazującą, czy wymagane jest ręczne adresowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="68e72-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="68e72-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="68e72-125">maxBufferPoolSize</span></span>|<span data-ttu-id="68e72-126">Pobiera lub ustawia maksymalny rozmiar w bajtach żadnych pul buforu używany przez transportu.</span><span class="sxs-lookup"><span data-stu-id="68e72-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="68e72-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="68e72-127">maxBufferSize</span></span>|<span data-ttu-id="68e72-128">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="68e72-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="68e72-129">Komunikaty przesyłane strumieniowo ta wartość powinna być co najmniej maksymalny rozmiar nagłówków wiadomości, które są odczytywane w tryb buforowany w.</span><span class="sxs-lookup"><span data-stu-id="68e72-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="68e72-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="68e72-130">maxOutputDelay</span></span>|<span data-ttu-id="68e72-131">Pobiera lub ustawia maksymalny interwał czasu, przez jaki fragmentów wiadomości lub cały komunikat może być buforowany w pamięci, zanim wysyłane.</span><span class="sxs-lookup"><span data-stu-id="68e72-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="68e72-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="68e72-132">maxPendingAccepts</span></span>|<span data-ttu-id="68e72-133">Pobiera lub ustawia maksymalną liczbę kanałów, o których usługa może mieć oczekiwanie na odbiornik do przetwarzania przychodzących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="68e72-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="68e72-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="68e72-134">maxPendingConnections</span></span>|<span data-ttu-id="68e72-135">Pobiera lub ustawia maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="68e72-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="68e72-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="68e72-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="68e72-137">Pobiera i ustawia maksymalny dozwolony rozmiar komunikatu, w bajtach, które mogą być odbierane.</span><span class="sxs-lookup"><span data-stu-id="68e72-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="68e72-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="68e72-138">transferMode</span></span>|<span data-ttu-id="68e72-139">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="68e72-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="68e72-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="68e72-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="68e72-141">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="68e72-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68e72-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="68e72-142">Parent Elements</span></span>  
  
|<span data-ttu-id="68e72-143">Element</span><span class="sxs-lookup"><span data-stu-id="68e72-143">Element</span></span>|<span data-ttu-id="68e72-144">Opis</span><span class="sxs-lookup"><span data-stu-id="68e72-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68e72-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="68e72-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="68e72-146">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="68e72-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68e72-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68e72-147">Remarks</span></span>  
<span data-ttu-id="68e72-148">Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu.</span><span class="sxs-lookup"><span data-stu-id="68e72-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="68e72-149">Inne składniki identyfikatora URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="68e72-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="68e72-150">`namedPipeTransport` Element jest punktem wyjścia do tworzenia niestandardowego powiązania, który implementuje protokół transportowy nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="68e72-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="68e72-151">Tego transportu jest używany dla na komputerze Windows Communication Foundation (WCF) - do - komunikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="68e72-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e72-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68e72-152">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="68e72-153">Transporty</span><span class="sxs-lookup"><span data-stu-id="68e72-153">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="68e72-154">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="68e72-154">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="68e72-155">Powiązania</span><span class="sxs-lookup"><span data-stu-id="68e72-155">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="68e72-156">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="68e72-156">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="68e72-157">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="68e72-157">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="68e72-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="68e72-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
