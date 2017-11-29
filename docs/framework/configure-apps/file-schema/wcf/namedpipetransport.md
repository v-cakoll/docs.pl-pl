---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d2d4be08012c1d33341ddd17713903782027c31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="e7071-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="e7071-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="e7071-103">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e7071-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="e7071-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e7071-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e7071-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e7071-105">\<bindings></span></span>  
<span data-ttu-id="e7071-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e7071-106">\<customBinding></span></span>  
<span data-ttu-id="e7071-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e7071-107">\<binding></span></span>  
<span data-ttu-id="e7071-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="e7071-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7071-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7071-109">Syntax</span></span>  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7071-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7071-110">Attributes and Elements</span></span>  
<span data-ttu-id="e7071-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7071-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7071-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7071-112">Attributes</span></span>  
<span data-ttu-id="e7071-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7071-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7071-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7071-114">Child Elements</span></span>  
  
|<span data-ttu-id="e7071-115">Element</span><span class="sxs-lookup"><span data-stu-id="e7071-115">Element</span></span>|<span data-ttu-id="e7071-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e7071-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7071-117">limitu czasu channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="e7071-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="e7071-118">Pobiera lub ustawia <xref:System.TimeSpan> , który określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="e7071-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="e7071-119">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="e7071-119">ConnectionBufferSize</span></span>|<span data-ttu-id="e7071-120">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="e7071-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="e7071-121">parametru hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e7071-121">hostNameComparisonMode</span></span>|<span data-ttu-id="e7071-122">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="e7071-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="e7071-123">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="e7071-123">manualAddressing</span></span>|<span data-ttu-id="e7071-124">Pobiera lub ustawia wartość wskazującą, czy ręcznego adresowania wiadomości jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="e7071-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="e7071-125">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e7071-125">maxBufferPoolSize</span></span>|<span data-ttu-id="e7071-126">Pobiera lub ustawia maksymalny rozmiar w bajtach pulami buforu, używany przez transport.</span><span class="sxs-lookup"><span data-stu-id="e7071-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="e7071-127">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="e7071-127">maxBufferSize</span></span>|<span data-ttu-id="e7071-128">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="e7071-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="e7071-129">Dla strumienia wiadomości wartość ta powinna być co najmniej maksymalna liczba nagłówków komunikatów, które są odczytywane w tryb buforowany.</span><span class="sxs-lookup"><span data-stu-id="e7071-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="e7071-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="e7071-130">maxOutputDelay</span></span>|<span data-ttu-id="e7071-131">Pobiera lub ustawia maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowane w pamięci przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="e7071-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="e7071-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="e7071-132">maxPendingAccepts</span></span>|<span data-ttu-id="e7071-133">Pobiera lub ustawia maksymalną liczbę kanałów, usługa może mieć oczekiwanie na odbiornik na potrzeby przetwarzania przychodzących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="e7071-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="e7071-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e7071-134">maxPendingConnections</span></span>|<span data-ttu-id="e7071-135">Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e7071-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="e7071-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e7071-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="e7071-137">Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości, w bajtach, które mogą być odebrane.</span><span class="sxs-lookup"><span data-stu-id="e7071-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="e7071-138">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="e7071-138">transferMode</span></span>|<span data-ttu-id="e7071-139">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="e7071-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="e7071-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="e7071-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="e7071-141">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="e7071-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7071-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7071-142">Parent Elements</span></span>  
  
|<span data-ttu-id="e7071-143">Element</span><span class="sxs-lookup"><span data-stu-id="e7071-143">Element</span></span>|<span data-ttu-id="e7071-144">Opis</span><span class="sxs-lookup"><span data-stu-id="e7071-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7071-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e7071-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e7071-146">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e7071-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7071-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7071-147">Remarks</span></span>  
<span data-ttu-id="e7071-148">Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu.</span><span class="sxs-lookup"><span data-stu-id="e7071-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="e7071-149">Inne składniki identyfikatora URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e7071-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="e7071-150">`namedPipeTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="e7071-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="e7071-151">Ten transport jest używany dla na komputerze z systemem Windows Communication Foundation (WCF) - do - komunikacyjny WCF.</span><span class="sxs-lookup"><span data-stu-id="e7071-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7071-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7071-152">See Also</span></span>  
<span data-ttu-id="e7071-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="e7071-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="e7071-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="e7071-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="e7071-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="e7071-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="e7071-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="e7071-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="e7071-157">[Transporty](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="e7071-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="e7071-158">[Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="e7071-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="e7071-159">[Powiązania](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="e7071-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="e7071-160">[Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="e7071-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="e7071-161">[Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="e7071-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="e7071-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e7071-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
