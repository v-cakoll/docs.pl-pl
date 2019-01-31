---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e30fcd5952fadc3b6cf30cb352a3bb51c86cc117
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285932"
---
# <a name="namedpipetransport"></a><span data-ttu-id="8f31d-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="8f31d-101">\<namedPipeTransport></span></span>
<span data-ttu-id="8f31d-102">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8f31d-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="8f31d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8f31d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8f31d-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8f31d-104">\<bindings></span></span>  
<span data-ttu-id="8f31d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8f31d-105">\<customBinding></span></span>  
<span data-ttu-id="8f31d-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8f31d-106">\<binding></span></span>  
<span data-ttu-id="8f31d-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="8f31d-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f31d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f31d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f31d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f31d-109">Attributes and Elements</span></span>  
<span data-ttu-id="8f31d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f31d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f31d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f31d-111">Attributes</span></span>  
<span data-ttu-id="8f31d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="8f31d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f31d-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f31d-113">Child Elements</span></span>  
  
|<span data-ttu-id="8f31d-114">Element</span><span class="sxs-lookup"><span data-stu-id="8f31d-114">Element</span></span>|<span data-ttu-id="8f31d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8f31d-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f31d-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8f31d-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="8f31d-117">Pobiera lub ustawia <xref:System.TimeSpan> określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="8f31d-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="8f31d-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8f31d-118">ConnectionBufferSize</span></span>|<span data-ttu-id="8f31d-119">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="8f31d-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="8f31d-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="8f31d-120">hostNameComparisonMode</span></span>|<span data-ttu-id="8f31d-121">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8f31d-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="8f31d-122">opcję manualAddressing</span><span class="sxs-lookup"><span data-stu-id="8f31d-122">manualAddressing</span></span>|<span data-ttu-id="8f31d-123">Pobiera lub ustawia wartość wskazującą, czy wymagane jest ręczne adresowanie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8f31d-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="8f31d-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8f31d-124">maxBufferPoolSize</span></span>|<span data-ttu-id="8f31d-125">Pobiera lub ustawia maksymalny rozmiar w bajtach żadnych pul buforu używany przez transportu.</span><span class="sxs-lookup"><span data-stu-id="8f31d-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="8f31d-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8f31d-126">maxBufferSize</span></span>|<span data-ttu-id="8f31d-127">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="8f31d-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="8f31d-128">Komunikaty przesyłane strumieniowo ta wartość powinna być co najmniej maksymalny rozmiar nagłówków wiadomości, które są odczytywane w tryb buforowany w.</span><span class="sxs-lookup"><span data-stu-id="8f31d-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="8f31d-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8f31d-129">maxOutputDelay</span></span>|<span data-ttu-id="8f31d-130">Pobiera lub ustawia maksymalny interwał czasu, przez jaki fragmentów wiadomości lub cały komunikat może być buforowany w pamięci, zanim wysyłane.</span><span class="sxs-lookup"><span data-stu-id="8f31d-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="8f31d-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8f31d-131">maxPendingAccepts</span></span>|<span data-ttu-id="8f31d-132">Pobiera lub ustawia maksymalną liczbę kanałów, o których usługa może mieć oczekiwanie na odbiornik do przetwarzania przychodzących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="8f31d-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="8f31d-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8f31d-133">maxPendingConnections</span></span>|<span data-ttu-id="8f31d-134">Pobiera lub ustawia maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="8f31d-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="8f31d-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8f31d-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="8f31d-136">Pobiera i ustawia maksymalny dozwolony rozmiar komunikatu, w bajtach, które mogą być odbierane.</span><span class="sxs-lookup"><span data-stu-id="8f31d-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="8f31d-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="8f31d-137">transferMode</span></span>|<span data-ttu-id="8f31d-138">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="8f31d-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="8f31d-139">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="8f31d-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="8f31d-140">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="8f31d-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f31d-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f31d-141">Parent Elements</span></span>  
  
|<span data-ttu-id="8f31d-142">Element</span><span class="sxs-lookup"><span data-stu-id="8f31d-142">Element</span></span>|<span data-ttu-id="8f31d-143">Opis</span><span class="sxs-lookup"><span data-stu-id="8f31d-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f31d-144">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8f31d-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8f31d-145">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8f31d-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f31d-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f31d-146">Remarks</span></span>  
<span data-ttu-id="8f31d-147">Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu.</span><span class="sxs-lookup"><span data-stu-id="8f31d-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="8f31d-148">Inne składniki identyfikatora URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8f31d-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="8f31d-149">`namedPipeTransport` Element jest punktem wyjścia do tworzenia niestandardowego powiązania, który implementuje protokół transportowy nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="8f31d-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="8f31d-150">Tego transportu jest używany dla na komputerze Windows Communication Foundation (WCF) - do - komunikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="8f31d-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f31d-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f31d-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8f31d-152">Transporty</span><span class="sxs-lookup"><span data-stu-id="8f31d-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="8f31d-153">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="8f31d-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="8f31d-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8f31d-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8f31d-155">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="8f31d-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8f31d-156">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="8f31d-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8f31d-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8f31d-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
